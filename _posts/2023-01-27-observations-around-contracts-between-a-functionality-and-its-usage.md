---
layout: post
title: Observations around a functionality and its usage
subtitle: A thought around contract testing and its relevance in Software Engineering
cover-img: /assets/img/path.jpg
share-img: /assets/img/path.jpg
tags: [Technology, Software Engineering, Contract Testing]
---

**Problem**

How would you feel as a Software Engineer if you write a function and mistakenly call it incorrectly in some other part of the code. For example forget to supply
a parameter etc. You would expect your IDE to *immediately highlight* the red squiggly line below the incorrect usage. But what if your IDE refuses to do it?
Then I assume you would fall back running the compiler and see the error that way but at the cost of a slow feedback loop which will eventually reduce your productivity.\
let's assume a hypothetical case where you are playing with a very immature language which has a dodgy compiler which doesn't even highlight such mistakes at
compile time. you'll eventually see problems at run time. What a nightmare, isn't it? Scripting languages have this problem but they try to compensate for this cost of
slower feedback by removing the compiler layer completely and letting your code execute as you make the change to it. but that's a different topic.

As your application becomes complex, this compile time checking of correct invocation disappears  when you decide to separate the functionality
and its invocation/usage into separate services sitting in different runtimes environments. This sounds like a very common scenario (microservices), isn't it?
We write microservices so much now-a-days that we forget this contract aspect of their communication. Default answer to that is integration testing but is that
really targeted towards the contract aspect? On top of that, integration tests are costly so you need to have both applications alive.
 
 **Solution**
 
So what is the solution now? there is no super compiler sitting on network level which can check if the API endpoint expects a different request or if  the response
object returned from this endpoint has changed. At present, one of the answers is contract testing which lets you check this exact requirement when you compile/build
either project (producer or consumer). [Pact](https://docs.pact.io/) and [Spring Cloud Contract](https://docs.spring.io/spring-cloud-contract/docs/current/reference/html/getting-started.html#getting-started-introducing-spring-cloud-contract) are some tools i know.
It's not as fast as your IDE tells immediately but at least it saves you from deploying the application with this mismatch between functionality and its usage.
