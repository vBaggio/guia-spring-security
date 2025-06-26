# 🚀 Spring Security

# 📚 Introdução ao Spring Security

## O que é ?

Spring Security é um framework de segurança poderoso e flexível que faz parte do ecossistema Spring. De forma simplificada, ele funciona como um guarda costas que protege sua aplicação, permitindo que você controle quem pode entrar e o que cada pessoa pode fazer quando estiver dentro do sistema.

## O que ele faz na prática?

Imagine o Spring Security como um sistema de segurança completo para sua aplicação. Ele:

- Protege suas rotas e APIs, impedindo que usuários não autorizados acessem informações sensíveis;
- Verifica a identidade dos usuários (autenticação), garantindo que eles são realmente quem dizem ser;
- Define o que cada usuário pode fazer no sistema (autorização), baseado em funções ou permissões;
- Defende sua aplicação contra ataques comuns na web, como:
    - CSRF (Cross-Site Request Forgery) - quando um site malicioso tenta fazer ações em nome do usuário;
    - XSS (Cross-Site Scripting) - quando códigos maliciosos são injetados em páginas web;
    - Injeção de cabeçalhos - manipulação indevida de informações enviadas ao servidor.
- Se conecta facilmente com diferentes sistemas de login, como:
    - LDAP - usado em ambientes corporativos;
    - OAuth2 - aquele botão de "Login com Google/Facebook";
    - JWT (JSON Web Tokens) - tokens modernos para APIs.

## Por que usar Spring Security em vez de criar sua própria solução?

Desenvolver um sistema de segurança do zero é como tentar construir seu próprio cofre bancário - complicado e arriscado! O Spring Security oferece vantagens importantes:

### 1. Segurança já testada e aprovada

Milhares de aplicações no mundo todo usam o Spring Security. Isso significa que muitos olhos já verificaram o código, encontraram falhas e as corrigiram. É como morar em um condomínio com segurança profissional em vez de tentar proteger sua casa sozinho.

### 2. Configuração simples e direta

Você pode configurar a segurança usando anotações (@Secured, @PreAuthorize) ou configurações em Java/XML. É como ter um painel de controle para a segurança da sua aplicação, em vez de precisar mexer na fiação elétrica.

### 3. Integração perfeita com Spring

Se você já usa Spring Boot, Spring MVC ou qualquer outra ferramenta Spring, o Security se encaixa como uma peça de quebra-cabeça. Não há atrito ou incompatibilidades para resolver.

### 4. Soluções prontas para uso

Precisa de uma tela de login? Autenticação com banco de dados? Login via redes sociais? O Spring Security já tem isso pronto. É como comprar um bolo pronto em vez de ter que reunir ingredientes e seguir uma receita.

### 5. Personalizável quando necessário

Apesar de ter muitas coisas prontas, você pode adaptar quase qualquer aspecto para atender às necessidades específicas do seu projeto. O framework oferece interfaces bem definidas que você pode implementar à sua maneira.

### 6. Sempre atualizado contra novas ameaças

O mundo digital está em constante evolução, e novos tipos de ataques surgem regularmente. A equipe do Spring Security trabalha continuamente para proteger as aplicações contra essas novas ameaças, lançando atualizações que você pode aplicar facilmente.

### 7. Comunidade ativa e documentação rica

Enfrentou um problema? Provavelmente alguém já passou por isso antes. A comunidade Spring é enorme, com fóruns ativos, tutoriais e uma documentação detalhada que ajuda a resolver qualquer dificuldade que você encontre.

# 🏗️ Arquitetura do Spring Security

## Visão geral da arquitetura

O Spring Security é construído sobre princípios sólidos de design, com uma arquitetura em camadas que separa claramente as responsabilidades. Imagine-o como um edifício de segurança bem projetado:

- O **Authentication Core** (núcleo de autenticação) verifica a identidade dos usuários, como um balcão de recepção onde você apresenta seu crachá;
- O **Authorization System** (sistema de autorização) determina o que você pode fazer depois de entrar, como um conjunto de portas que só abrem para quem tem a permissão certa;
- Os **Security Filters** inspecionam cada solicitação antes que ela chegue à sua aplicação, como guardas que verificam cada pessoa que tenta entrar no prédio.

Esta arquitetura em camadas permite que o Spring Security seja ao mesmo tempo robusto e flexível - você pode substituir ou estender partes específicas sem desmontar todo o sistema.

## Como o Spring Security se integra ao Spring Framework

A integração do Spring Security com o resto do ecossistema Spring é praticamente perfeita, funcionando como um módulo que se encaixa naturalmente no framework principal:

- Ele usa o mesmo sistema de **Dependency Injection** (injeção de dependências), permitindo que você conecte seus próprios componentes de segurança quando necessário;
- Aproveita o padrão **Aspect-Oriented Programming (AOP)** do Spring para aplicar segurança de forma declarativa, sem poluir seu código de negócios;
- Integra-se automaticamente com o **Spring MVC** para proteger controllers e endpoints;
- Funciona perfeitamente com o **Spring Boot**, oferecendo **Auto-configuration** que detecta o que você está usando e configura a segurança apropriadamente;
- Compartilha o mesmo modelo de **Events e Listeners**, permitindo que sua aplicação reaja a eventos de segurança (como login bem-sucedido ou falha de autenticação).

Esta integração profunda significa que você não precisa de adaptadores ou "cola" extra para fazer o Spring Security funcionar com seus projetos Spring existentes - ele simplesmente se torna parte do ecossistema, como se sempre estivesse lá.

## O fluxo de uma requisição através do Spring Security

O diagrama a seguir representa o fluxo simplificado de uma requisição HTTP feita para uma aplicação Spring contando com o Spring Security devidamente configurado para realizar a autenticação e autorização do usuário:
![[assets/arquitetura-diagrama-1.svg]]
Vamos entender esse fluxo passo a passo:

1. A requisição chega à aplicação e logo é interceptada pelo Spring Security;
2. Para que a requisição seja permitida, ela precisa passar por uma série de filtros de segurança, para garantir que o usuário possui as devidas permissões para acessar o recurso. Esse é o papel do **Security Filter Chain**.
3. No exemplo simplificado, temos dois filtros: Autenticação e Autorização. A ideia é verificar se o usuário está logado e possui o direito de acesso ao recurso solicitado.
4. Podemos definir quantos filtros personalizados quisermos, especificar quais recursos são públicos ou privados, criar múltiplos níveis de acesso por usuário, esse é o poder do **Security Filter Chain**.
5. Caso algum falhe um dos filtros de Autenticação ou Autorização, o Spring Security se encarrega de barrar a requisição devolvendo um status **401 Unauthorized** ou **403 Forbidden**, respectivamente.
6. Após a autenticação bem-sucedida, o **Security Context** é estabelecido, mantendo as informações do usuário durante o ciclo de vida da requisição;
7. Agora segue-se o fluxo normal da aplicação, conforme definido no Rest Controller.

Com esta arquitetura robusta e integração perfeita, o Spring Security se torna não apenas uma ferramenta, mas uma extensão natural do seu desenvolvimento com Spring, tornando a segurança uma parte intrínseca da sua aplicação em vez de algo adicionado posteriormente.

