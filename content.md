O que é Async Storage?

Async Storage é como uma caixa mágica onde seu aplicativo pode guardar coisas e depois pegar essas coisas de volta. Imagine que você tem um baú do tesouro, e pode guardar e encontrar seus brinquedos a qualquer momento. Isso é o que o Async Storage faz para os dados no seu app!


Como inserir dados e recuperar

Guardar algo no Async Storage é como colocar um brinquedo no baú. Quando lidamos com objetos, precisamos transformar eles em uma string (usando JSON.stringify) para guardar e depois transformar de volta em objeto (usando JSON.parse) para pegar. Isso é porque o Async Storage só entende strings, não objetos diretamente.

javascript
Copiar código
import AsyncStorage from '@react-native-async-storage/async-storage';

const guardarDados = async (chave, valor) => {
  try {
    await AsyncStorage.setItem(chave, valor);
  } catch (e) {
    console.log('Erro ao guardar dados:', e);
  }
};

guardarDados('meuBrinquedo', 'carrinho de corrida');
Para pegar seu brinquedo de volta:

javascript
Copiar código
const pegarDados = async (chave) => {
  try {
    const valor = await AsyncStorage.getItem(chave);
    if (valor !== null) {
      console.log('Achei o brinquedo:', valor);
    }
  } catch (e) {
    console.log('Erro ao pegar dados:', e);
  }
};

pegarDados('meuBrinquedo');  // Saída: Achei o brinquedo: carrinho de corrida



Limitações do Async Storage

Async Storage é ótimo para guardar dados localmente no seu aplicativo, mas ele tem algumas limitações que você deve conhecer.

Async Storage não é super rápido quando você tem muitos dados para guardar ou recuperar. Isso acontece porque, conforme a quantidade de dados aumenta, o tempo necessário para ler e escrever esses dados também cresce. É como se você estivesse tentando encontrar um brinquedo em um baú muito cheio: fica mais difícil e demorado. Além disso, a quantidade de dados que você pode guardar no Async Storage pode ser limitada pelo dispositivo. Isso varia de um dispositivo para outro, mas geralmente, o espaço disponível é menor do que o de uma base de dados completa. É como se seu baú tivesse um tamanho máximo; se você tentar colocar mais brinquedos do que ele pode suportar, não vai caber.

Alternativas

Se você precisar guardar muitos dados ou dados maiores, existem alternativas mais eficientes:

• SQLite: É como um armário maior e mais organizado para guardar seus dados. Ele pode lidar com grandes quantidades de dados de forma mais eficiente.
• Secure Storage: É como um cofre, muito seguro para guardar dados sensíveis, como senhas ou informações pessoais importantes.

Quer saber mais sobre como fazer seu app ser incrível? Siga no LinkedIn

#AsyncStorage #DesenvolvimentoMobile #ReactNative