+++
date = '2026-02-13'
draft = false
title = 'Botnet atacando meu blog'
lead = 'Ainda bem que eu não tô usando WordPress'
thumbnail = '/img/wordpress-bots.png'
tags = ['tecnologia', 'internet', 'selfhosting']
+++

Quando eu subi esse blog a primeira vez via web server, fui acompanhar os logs e estranhei a presença de algumas requisições. Porra, eu tinha acabado de subir o site, como que já tinha alguém acessando?

Analisando o endpoint que as requisições estavam tentando acessar, aí saquei que na verdade era tudo **botnet**.

É óbvio que isso não acontece só comigo, mas com qualquer serviço que esteja exposto na internet. O tempo inteiro.

Mas tá tudo certo porque meu blog é **estático**.

<!--more-->

[![logs do nginx](/img/wordpress-bots.png)](/img/wordpress-bots.png)

A maioria dessas requisições são tentativas de verificar se existem endpoints de administração de algum CMS, como o Wordpress, ou de qualquer serviço que possa deixar uma API ou uma página de login exposta.

Caso alguma dessas requisições seja bem sucedida, o bot provavelmente marca o site para explorar e tentar atacar o serviço de alguma forma.

Quando eu tive a ideia inicial de criar o blog, eu logo pensei em usar o WordPress, afinal era o único CMS que eu conhecia de fato. Mas no meu contexto, de estar hospedando o web server da minha própria máquina, servir arquivos de html estáticos era a melhor opção pra evitar dor de cabeça. Afinal, eu só quero ter um espaço pra falar do que der na telha.

Manter um blog em Wordpress exigiria estar ligado em novas vulnerabilidades e manter o sistema atualizado.

Aqui no blog não há nenhum código php ou javascript rodando, não há nenhum banco de dados. São só arquivos html, css e estáticos que são servidos conforme o visitante navega pelo site. Não tem nada dinâmico, ou sendo processado num backend. Não tem login de usuário, não tem painel de administração.

Então por isso, eu posso simplesmente olhar esses logs e ficar de boa. Que se foda, vão arrumar nada aqui.

Claro que também por estar servindo o blog também por meio de um [CloudFlare Tunnel](https://developers.cloudflare.com/cloudflare-one/networks/connectors/cloudflare-tunnel/), eu tenho uma camada extra de proteção, já que o CloudFlare bloqueia a maioria dessas requisições antes mesmo de chegar no meu servidor (principalmente as de crawlers de IA).

A única interação que eu gostaria de implementar aqui no futuro, é a função de comentários. Mas ainda não tô esquentando a cabeça com isso.

No fim das contas, não é nenhuma surpresa ver mais um indício de que a maior parte do tráfego da internet atual, é gerado por bots. Mas é massa demais poder ver exatamente como a botnet atua e não deixa escapar nem meu recém nascido lugarzinho na web.
