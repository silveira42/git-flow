# Git Flow (pt-br)
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/silveira42/git-flow/blob/main/README.md)
[![pt-br](https://img.shields.io/badge/lang-pt--br-green.svg)](https://github.com/silveira42/git-flow/blob/main/LEIAME.md)

## Introdução
Imagine que você desenvolveu um aplicativo de celular e o subiu para a loja de aplicativos.

Tudo está indo bem, você começa a ganhar novos usuários até que chega uma notificação de que um dos usuários reportou um bug no seu aplicativo.

E agora? Como você vai consertar esse bug que está em produção?

Surge a ideia seguinte: "Vou copiar e colar a pasta em que está o meu código, rodá-lo em minha máquina para conseguir testar, e quando consertar o bug eu faço as mesmas mudanças em produção".

Sem perceber, você criou o conceito de uma *__branch__*.

## Conceitos (branch, pull request)

### O que é uma branch?

Uma branch é somente uma pasta que contém uma versão do seu código.

Agora o seu aplicativo tem duas versões: Uma versão que está liberada para o público geral, ou seja, em produção, e uma versão que voce mantém na sua máquina para fazer melhorias e corrigir bugs.

Porém uma branch no git tem funcionalidades que uma pasta local não tem, como: 
- Manutenção de todo o histórico de mudanças
- Capacidade de automaticamente juntar branches
- Possibilidade de usar um host (como o Github, Gitlab, Bitbucket...) para que mais de uma pessoa possa ter acesso a mesma versão do código.

### O que é um pull request?
Um Pull Request é uma funcionalidade de hosts de Git para momentos em que voce quer juntar o código que está em uma branch com o código que está em outra branch de forma mais segura e controlada.

Ao fazer um Pull Request ele passará por um processo de revisão que pode ser configurado para requerir aprovação de X pessoas antes que o código de fato seja adicionado à branch que está recebendo o Pull Request..

### O que eu não preciso entender agora?

_Como o git mantém o histórico do seu código?_

_Como ele sabe o que manter e o que substituir quando você faz um Pull Request?_

O funcionamento do git é algo complexo a primeira vista, pois o Git é uma ferramenta prática. Perguntas como essas, por mais que interessantes, podem atrapalhar o entendimento mais simples das funcionalidades dele.

A minha sugestão é que tente deixar de lado essas questões temporariamente. A maior parte das coisas sobre o git voce só entenderá na prática.

Após ter o costume de usá-lo fluentemente, aí sim apresenta-se uma boa oportunidade para entender as complexidades embaixo dos panos.

## Fluxo em si
O fluxo inicia-se no cenário ideal em que se tem as branches:
- main (produção)
- hom (homologação)
- dev (desenvolvimento)

Cada uma dessas branches deve representar um ambiente em que o seu aplicativo funciona.

> Caso não haja ambiente de homologação, não deve haver branch de homologação, mas mesmo que não haja ambiente de dev se faz interessante ter uma branch de dev.

Ao querer adicionar uma feature ou resolver um bug, devemos puxar/criar uma nova branch a partir da **main**.

O nome da branch deve ser curto, mas descritivo. Duas ou tres palavras que te fazem lembrar o que está sendo feito alí.

É boa prática colocar sempre a palavra mais genérica primeiro.

> Ao invés de botao-cadastro-home, home-cadastro-botao. Dessa forma todas as branches referentes à home estarão próximas e indexáveis por ordem alfabética. Também estarão assim juntas as branches específicas sobre o cadastro na home, como a home-cadastro-logo por exemplo.

Dentro dessa branch, devem ser feitos commits sempre que uma parte da mudança foi concluída, ou quando for parar de trabalhar nela por várias horas.

É importante comitar antes de pausar o trabalho para que as outras pessoas no mesmo projeto vejam sempre a versão mais atualizada.

Quando a feature está concluída, deve ser feito um merge da branch específica na branch de dev, assim registrando a entrega do desenvolvimento.

Para subir a branch e suas mudanças para o ambiente de homologação, deve-se seguir o passo a passo:
1. Entrar na branch de homologação `git checkout hom`.
2. Juntar as duas branches `git merge home-cadastro-botao`.
3. Resolver merge conflicts, se houver.
4. Compilação do código no ambiente de homologação/criação de nova build.
5. Subida das mudanças ao host (ex. Github) `git push origin hom`

Já para subir a branch em ambiente de produção usaremos o Pull Request, por ser mais controlado e seguro.
1. No site do Github entrar no repositório desejado e na branch desejada
2. Clicar em "Fazer um Pull Request"
3. Descrever a mudança feita
4. Enviar o Pull Request

O Pull Request criado será revisado e posteriormente aprovado.

<!--## Exemplos práticos-->


<!--## Exercícios-->
