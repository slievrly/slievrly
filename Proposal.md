### Abstract

Seata(Simple Extensible Autonomous Transaction Architecture) is an easy-to-use and high-performance distributed transaction solution, used to solve the data consistency problem.


### Proposal
Seata has a fairly huge community. It is widely adopted by many companies and organizations, but most of them are in China. We believe running Seata in Apache Software Foundation can facilitate development of a stronger and more diverse community.

Alibaba and Ant Group submit this proposal to donate Seata's source code and its side projects to the Apache Software Foundation. The code is already under the Apache License Version 2.0. Seata source code and its side projects are hosted on github right now:

- Seata code base:
    - https://github.com/seata/seata （Java）
    - https://github.com/seata/seata-go (Golang)
- Documentations/WebSite: https://github.com/seata/seata.github.io
- Samples: https://github.com/seata/seata-samples
- Other side projects hosted under [seata group](https://github.com/seata)

### Background

With the evolution of technology architecture, data consistency becomes an insoluble technical problem when businesses use microservice architecture. Seata originated from the practical experience gained by Alibaba and Ant Group in their internal business scenarios.

Here is the history of this project:

1. Alibaba and Ant Group have internally developed a data middleware to solve the consistency of business application data for e-commerce, payment, logistics and other business scenarios. This middleware can be traced back to 2007 and has been internally applied for over 10 years. The internal project is called TXC (Taobao Transaction Constructor)/XTS (eXtended Transaction Service). The project is used in almost every order and payment.

2. Since 2013, Alibaba and Ant Group have released GTS(global transaction service)/DTX(Distributed Transaction-eXtended), a distributed transaction cloud service product, to external customers on Alibaba Cloud and Financial Cloud. They have accumulated a large number of users in various industry sectors.

3. In January 2019, Alibaba Group officially launched the project and named it Fescar (Fast & Easy Commit and Rollback). Since then, it has been warmly welcomed and praised by numerous developers, and once ranked first in the GitHub trending List.

4. In April 2019, Ant Group joined in Fescar. In order to create a more open and neutral community, Fescar was renamed as Seata and migrated from the Alibaba organization to its independent organization.

We'd like to share this outstanding framework at the Apache Software Foundation, and build a more diverse community by following the Apache way. We believe more people and organizations can be benefit from it by doing so.


### Rationale
Before Seata was introduced, developers primarily resolved data consistency problems in the application architecture by adopting eventual consistency. However, there were challenges including high business invasiveness, poor synchronization interactivity, and weak data isolation. Seata can resolve various types of data consistency scenarios, including single applications with multiple databases, cross-microservice interactions, and multiple different types of resources. Currently, Seata provides several transaction patterns, including AT (Automatic Transaction), TCC (Try-Confirm-Cancel), Saga ([Sagas](http://www.amundsen.com/downloads/sagas.pdf)), and XA(eXtended Architecture). Seata not only supports strong consistency for synchronous calls but also facilitates asynchronous eventually consistency based on events. Developers have the flexibility to choose one or more transaction patterns according to the requirements of their business scenarios.

Seata define a Distributed Transaction as a Global Transaction, which is made up with a batch of branch transactions. Typically, a branch transaction in Seata is a local transaction. There are three basic components in Seata:

1. TC(Transaction Coordinator): The TC component in Seata is an independent server responsible for maintaining the status of transactions. It drives the global transactions to either commit or rollback.
2. TM(Transaction Manager): The TM component in Seata is integrated into applications to define the scope of global transactions. It allows applications to begin a global transaction, as well as to commit or rollback a global transaction.
3. RM(Resource Manager): The RM component in Seata is integrated into applications to manage the resources that branch transactions are working on. It connects to the TC (Transaction Coordinator) to register branch transactions, report the status of branch transactions, and drive the branch transactions to commit or rollback.

Developers can easily use Seata annotations and configuration to meet the requirements of various scenarios of distributed transactions without code intrusion.


### Initial Goals
First and foremost, we aim to enlarge the community. Seata is already a diverse community, but we want to see more. Secondly, we have more ideas about transaction processing, such as exploring transaction patterns that balance consistency and performance, utilizing a combination of multiple transaction patterns, and implementing non-intrusive transaction patterns without code intrusion. We believe we can address some of these while an Apache Incubator project.

### Current Status
#### Meritocracy
The intent of this proposal is to start building a diverse developer and user community around Seata following the Apache way. Since Seata was open-sourced, we have actively sought contributions through our website and presentations to user groups and technical audiences. We have received positive feedback and valuable contributions from the community. Furthermore, we have established the Maintainer and Committer Team to oversee the project's development and maintenance. New contributors are guided and reviewed by active Committer members. When they are ready, Maintainer will start a vote to promote him/her to become a member of Committer Team. Contributions are always welcomed and highly valued. We plan to continue supporting new contributors and collaborating with those who make significant contributions to the project, encouraging them to become committers.

#### Community

Seata is being developed by the development team inside Alibaba who's responsible for building internal distributed 
system too. Since Seata was open-sourced on GitHub, it has gained significant traction, receiving up to 24k stars, 
being forked over 8k times, and having more than 40 versions released. Besides being widely adopted inside Alibaba 
and Ant Group, Seata is also widely adopted by hundreds of other companies, including EVERBRIGHT Bank(cebbank.com), 
China EMS (China Express Mail Service, ems.com.cn), China Tower(china-tower.com), China Unicom(chinaunicom.com.cn), 
China Southern Airlines(csair.com), China TravelSky(travelsky.cn), Meituan(meituan.com), Didi (didiglobal.com), 
shopee(shopee.cn), 360(360.cn), 58 city net(58.com), iFLYTEK(global.iflytek.com), ViVo(vivo.com.cn), XiaoPeng
(xiaopeng.com), Beke(bj.ke.com), ZTO Express(zto.com), YunDa Express(yundaex.com), Haier(haier.com), TCL(tcl.com) and many more. For more information, please [click here](https://github.com/seata/seata/issues/1246). We aim to expand the contributor by inviting all those who make valuable contributions and excel in adhering to The Apache Way. The Seata project and its side projects always accept contributions from individuals outside of Alibaba. Currently, we utilize GitHub as our code hosting platform.



#### Core Developers
The core developers would come from both Alibaba and Ant Group. They include people who have been working on related projects and the creation of the Seata Community since the beginning. Additionally, the team also includes experienced open source developers newly contributing to the project. They have formed a group full of diversity.


### Known Risks
The project is well-known in the field of distributed transactions and Microservices, and has been live for over 4 years. We are not sure there exists a risk, but definitely have a challenge for us.

#### Orphaned products
Some core developers currently work full-time on the Seata project for Alibaba. Seata provides a critical internal infrastructure and has been in production use at Alibaba since 2013. In addition, Seata has been widely adopted by hundreds of companies for integration into their business systems. So there is no concern that it will become an orphaned product.


#### Inexperience with Open Source
The founder of the Seata community, Min Ji, is an open-source enthusiast who has actively participated in the open-source community for over 5 years. He has made contributions to numerous open-source projects, including Apache Dubbo, Nacos, Netty, Spring Cloud Alibaba, Mybatis, and RxJava.  
In addition, the core developers of the community include PMCs and committers from the Apache Dubbo community.


#### Homogenous Developers

The current group of developers involved in the project represents a diverse range of organizations, including Alibaba, Ant, TongDun, Tencent, Baidu, JD, 360, NetEase, Truthai, Helios, and HuiKang. Furthermore, many other companies forked Seata and continued to enhance in their own private repositories. We plan to encourage them to contribute and invite them as contributors to work on one common code base. The goal is to establish a vibrant developer community and we will actively encourage new contributors.

#### Reliance on Salaried Developers
Currently, only some of the core developers in Alibaba and Ant are paid to work on Seata. Salaried Developers is a very small group, and we have established a diverse developer community. We look forward to building a strong community around the project in order to encourage more contributors to join the project.


#### Relationships with Other Apache Products
- [Dubbo](https://dubbo.apache.org/): Seata supports distributed transactions using Dubbo service calls.
- [ShardingSphere](https://shardingsphere.apache.org/): ShardingSphere integrated Seata  to solve distributed transactions in the scenario of sharding databases and tables.
- [SkyWalking](https://skywalking.apache.org/): SkyWalking is a very important APM plugin for Seata.
- [ZooKeeper](https://zookeeper.apache.org/): ZooKeeper is a registry implementation of Seata.
- [RocketMQ](https://rocketmq.apache.org/): RocketMQ is a transaction resource supported by Seata in distributed transactions.
- [Kafka](https://kafka.apache.org/): Kafka is one of the log collection methods integrated by Seata.

In addition, Seata also relies on Apache products such as tomcat, httpcomponents.

#### An Excessive Fascination with the Apache Brand
While we respect the reputation of the Apache brand and have no doubt that it will attract new contributors and users, our interest is primarily to give Seata a solid home as an open source project following an established development model. More reasons are provided in the Rationale and Alignment sections.

### Documentation
A complete set of Seata documentations is provided on seata.io in both English and Simplified Chinese.
- [English](https://seata.io/en/)
- [Chinese](https://seata.io/zh-cn/)

### Initial Source
Seata was initially developed within Alibaba and later open-sourced under Alibaba Group on GitHub in 2019, using Apache-2.0 License. This open-source project was initially named Fescar. After Ant joined the Fescar community, it was renamed as Seata, and the relevant code repositories were migrated from the Alibaba organization to the Seata organization. Specifically, the initial source includes:

- Seata code base:
  - https://github.com/seata/seata （Java）
  - https://github.com/seata/seata-go (GoLang)
- Documentations/Website: https://github.com/seata/seata.github.io
- Samples: https://github.com/seata/seata-samples
- Other side projects hosted under [seata group](https://github.com/seata)


### Source and Intellectual Property Submission Plan
- Source:
  - The project has been licensed under Apache License 2.0. As soon as Seata is approved to join ASF incubator, we can transfer the source code and documentation to the Apache Foundation.
  - Currently, all artifacts are copyrighted by the 'Seata.io Organization' and are associated with the 'Seata.io' domain owned by Alibaba. The Seata community uses [Alibaba's ICLA](https://cla-assistant.io/seata/seata), with over 180 contributors having signed up for it, covering all core developers. There are no corporate developers involved other than Alibaba and Ant Group, so there is no need for a CCLA from any other companies besides Alibaba and Ant Group. After Seata is approved to enter the ASF Incubator, Alibaba and Ant Group will also sign the CCLA with ASF.

- Alibaba and Ant Group will sign the SGA (Software Grant Agreement) jointly with ASF.
- Domains: [seata.io](https://seata.io/),[demo.seata.io](http://demo.seata.io/) are all currently owned by Alibaba. Alibaba has completed the necessary preparations for transferring the domain name to ASF.
- Trademark: The Seata trademark is currently owned by Ant Group. Ant Group will proceed with the transfer of the trademark in accordance with the project graduation checklist.



#### External Dependencies

All dependencies have Apache compatible licenses except MySQL (GPL-2.0). We will remove MySQL dependency before the first release.


##### Seata console（front-end project）:
https://github.com/seata/seata/tree/develop/console/src/main/resources/static/console-fe
https://github.com/seata/seata/tree/develop/saga/seata-saga-statemachine-designer

- ISC
    - css-color-keywords@1.0.0
    - fs.realpath@1.0.0
    - wrappy@1.0.2
    - inflight@1.0.6
    - @antv/util@1.3.1
    - once@1.4.0
    - inherits@2.0.4
    - minimatch@3.1.2
    - glob-parent@5.1.2
    - glob@7.2.3

- MIT
    - @antv/scale@0.0.1
    - concat-map@0.0.1
    - isarray@0.0.1
    - @antv/attr@0.0.7
    - @antv/component@0.0.9
    - @alicloud/css-var-utils@0.1.0
    - is-arrayish@0.2.1
    - decode-uri-component@0.2.2
    - @emotion/weak-memoize@0.2.5
    - yamljs@0.3.0
    - @jridgewell/gen-mapping@0.3.1
    - asynckit@0.4.0
    - @emotion/memoize@0.7.4
    - @emotion/unitless@0.7.5
    - @emotion/hash@0.8.0
    - dagre@0.8.4
    - @emotion/stylis@0.8.5
    - @emotion/is-prop-valid@0.8.8
    - @emotion/sheet@0.9.4
    - delayed-stream@1.0.0
    - react-codemirror@1.0.0
    - style-equal@1.0.0
    - supports-preserve-symlinks-flag@1.0.0
    - camelize@1.0.1
    - path-is-absolute@1.0.1
    - shallow-element-equals@1.0.1
    - value-equal@1.0.1
    - @alicloud/console-components-actions@1.0.19
    - balanced-match@1.0.2
    - flatten@1.0.3
    - has@1.0.3
    - tiny-warning@1.0.3
    - escape-string-regexp@1.0.5
    - path-parse@1.0.7
    - combined-stream@1.0.8
    - find-root@1.1.0
    - is-stream@1.1.0
    - function-bind@1.1.1
    - @jridgewell/set-array@1.1.2
    - color-name@1.1.3
    - @alicloud/console-components-app-layout@1.1.4
    - @alifd/validate@1.2.3
    - tiny-invariant@1.3.1
    - error-ex@1.3.2
    - dva-core@1.4.0
    - loose-envify@1.4.0
    - resize-observer-polyfill@1.5.1
    - @alicloud/console-components@1.5.7
    - @alifd/field@1.5.8
    - path-to-regexp@1.8.0
    - color-convert@1.9.3
    - convert-source-map@2.0.0
    - to-fast-properties@2.0.0
    - is-plain-object@2.0.4
    - loader-utils@2.0.4
    - is-plain-obj@2.1.0
    - ms@2.1.2
    - babel-plugin-styled-components@2.1.4
    - graphlib@2.1.7
    - react-loading-skeleton@2.2.0
    - invariant@2.2.4
    - @alifd/meet-react/node_modules/classnames@2.2.6
    - @antv/g6@2.2.6
    - classnames@2.2.6
    - json-parse-even-better-errors@2.3.1
    - picomatch@2.3.1
    - css-to-react-native@2.3.2
    - fecha@2.3.3
    - dva@2.4.1
    - babel-plugin-macros@2.4.2
    - chalk@2.4.2
    - redux-thunk@2.4.2
    - merge-anything@2.4.4
    - jsesc@2.5.2
    - dom-to-image@2.6.0
    - @antv/gl-matrix@2.7.1
    - @alifd/meet-react@2.9.2
    - has-flag@3.0.0
    - resolve-from@3.0.0
    - resolve-pathname@3.0.0
    - react-lifecycles-compat@3.0.4
    - callsites@3.1.0
    - @jridgewell/resolve-uri@3.1.1
    - escalade@3.1.1
    - ansi-styles@3.2.1
    - import-fresh@3.3.0
    - postcss-value-parser@3.3.1
    - dom-helpers@3.4.0
    - @antv/g@3.4.6
    - stylis@3.5.4
    - jquery@3.6.0
    - core-js@3.6.5
    - form-data@4.0.0
    - js-tokens@4.0.0
    - parse-json@4.0.0
    - is-glob@4.0.3
    - warning@4.0.3
    - lodash.debounce@4.0.8
    - react-router-redux@4.0.8
    - object-assign@4.1.1
    - redux@4.2.0
    - react-router@4.3.1
    - react-router-dom@4.3.1
    - debug@4.3.4
    - styled-components@4.4.1
    - lodash.clonedeep@4.5.0
    - lodash.isequal@4.5.0
    - react-redux@5.1.2
    - safe-buffer@5.1.2
    - cosmiconfig@5.2.1
    - memoize-one@5.2.1
    - supports-color@5.5.0
    - bignumber.js@9.0.2
    - stylis-rule-sheet@0.0.10
    - @types/isomorphic-fetch@0.0.34
    - @emotion/utils@0.11.3
    - regenerator-runtime@0.14.0
    - @types/scheduler@0.16.3
    - scheduler@0.19.1
    - axios@0.27.2
    - @antv/hierarchy@0.3.15
    - @jridgewell/trace-mapping@0.3.19
    - iconv-lite@0.4.24
    - @types/d3-selection@1.0.10
    - argparse@1.0.10
    - brace-expansion@1.1.11
    - follow-redirects@1.15.3
    - @alicloud/console-components-console-menu@1.2.12
    - resolve@1.22.6
    - @jridgewell/sourcemap-codec@1.4.15
    - mime-db@1.52.0
    - babel-plugin-emotion@10.2.2
    - @emotion/core@10.3.1
    - create-react-class@15.7.0
    - @types/prop-types@15.7.7
    - prop-types@15.8.1
    - mime-types@2.1.35
    - is-core-module@2.13.0
    - commander@2.20.3
    - moment@2.29.4
    - csstype@2.6.20
    - is-what@3.14.1
    - history@4.10.1
    - @types/history@4.7.11
    - @types/react-router-redux@5.0.22
    - @types/react-router@5.1.20
    - codemirror@5.65.8
    - @babel/plugin-syntax-jsx@6.18.0
    - babel-plugin-syntax-jsx@6.18.0
    - babel-runtime@6.26.0
    - @babel/helper-annotate-as-pure@7.22.5
    - @babel/helper-hoist-variables@7.22.5
    - @babel/helper-split-export-declaration@7.22.6
    - @babel/core@7.23.0
    - @babel/generator@7.23.0
    - @babel/helper-function-name@7.23.0
    - @babel/parser@7.23.0
    - @babel/traverse@7.23.0
    - @babel/types@7.23.0
    - @babel/runtime@7.23.1
    - @emotion/serialize@0.11.16
    - dayjs@1.11.10
    - @alifd/next@1.24.18
    - @emotion/css@10.0.27
    - @emotion/cache@10.0.29
    - globals@11.12.0
    - react-is@16.12.0
    - react@16.14.0
    - react-dom@16.14.0
    - lodash@4.17.21
    - @babel/code-frame@7.22.13
    - @babel/helper-module-imports@7.22.15
    - @babel/template@7.22.15
    - @babel/helper-environment-visitor@7.22.20
    - @babel/helper-validator-identifier@7.22.20
    - @babel/highlight@7.22.20
    - @types/react@16.14.46

- Unlicense
    - wolfy87-eventemitter@5.2.8

- Apache-2.0
    - d3-svg-legend@2.25.6

- BSD-2-Clause
    - esprima@4.0.1

- BSD-3-Clause
    - d3-sankey@0.7.1
    - sprintf-js@1.0.3
    - d3-chord@1.0.6
    - d3-dispatch@1.0.6
    - d3-ease@1.0.6
    - d3-polygon@1.0.6
    - d3-collection@1.0.7
    - d3-quadtree@1.0.7
    - d3-path@1.0.9
    - d3-time@1.1.0
    - d3-fetch@1.1.2
    - d3-random@1.1.2
    - d3-voronoi@1.1.4
    - d3-brush@1.1.5
    - d3-interpolate@1.1.6
    - d3-hierarchy@1.1.9
    - d3-dsv@1.2.0
    - d3-force@1.2.1
    - d3-array@1.2.4
    - d3-drag@1.2.5
    - d3-contour@1.3.2
    - d3-transition@1.3.2
    - rw@1.3.3
    - d3-shape@1.3.7
    - d3-color@1.4.0
    - d3-selection@1.4.1
    - d3-format@1.4.2
    - d3-scale-chromatic@1.5.0
    - d3-zoom@1.8.3
    - d3-scale@2.2.2
    - d3-time-format@2.2.2
    - react-transition-group@2.9.0
    - hoist-non-react-statics@3.3.2
    - flat@5.0.2
    - d3-timer@1.0.10
    - d3-axis@1.0.12
    - d3-geo@1.11.9
    - d3@5.14.2



##### seata/seata
https://github.com/seata/seata/tree/develop

- Apache-1.1
    - com.caucho:hessian@4.0.63

- Apache-2.0
    - io.protostuff:protostuff-api@1.5.9
    - io.protostuff:protostuff-collectionschema@1.5.9
    - io.protostuff:protostuff-core@1.5.9
    - io.protostuff:protostuff-runtime@1.5.9
    - com.fasterxml.jackson.datatype:jackson-datatype-jsr310@2.11.4
    - org.apache.ant:ant@1.10.12
    - org.apache.ant:ant-launcher@1.10.12
    - javax.inject:javax.inject@1
    - commons-logging:commons-logging@1.2
    - com.google.j2objc:j2objc-annotations@1.3
    - commons-jxpath:commons-jxpath@1.3
    - commons-pool:commons-pool@1.6
    - com.github.vlsi.compactmap:compactmap@2.0
    - org.yaml:snakeyaml@2.0
    - joda-time:joda-time@2.3
    - commons-lang:commons-lang@2.6
    - commons-io:commons-io@2.7
    - org.objenesis:objenesis@3.3
    - net.logstash.logback:logstash-logback-encoder@6.5
    - com.101tec:zkclient@0.11
    - de.javakaffee:kryo-serializers@0.45
    - commons-configuration:commons-configuration@1.10
    - commons-codec:commons-codec@1.15
    - org.apache.commons:commons-compress@1.21
    - org.yaml:snakeyaml@1.28
    - org.jetbrains:annotations@13.0
    - com.netflix.netflix-commons:netflix-eventbus@0.3.0
    - com.netflix.netflix-commons:netflix-infix@0.3.0
    - io.etcd:jetcd-common@0.5.0
    - io.etcd:jetcd-core@0.5.0
    - io.etcd:jetcd-resolver@0.5.0
    - org.apache.yetus:audience-annotations@0.5.0
    - io.prometheus:simpleclient_httpserver@0.6.0
    - com.netflix.archaius:archaius-core@0.7.6
    - com.google.guava:failureaccess@1.0.1
    - org.apache.dubbo.extensions:dubbo-filter-seata@1.0.2
    - com.typesafe:config@1.2.1
    - com.alibaba:druid@1.2.7
    - org.codehaus.jettison:jettison@1.4.0
    - com.alibaba.nacos:nacos-api@1.4.2
    - com.alibaba.nacos:nacos-client@1.4.2
    - com.alibaba.nacos:nacos-common@1.4.2
    - com.ecwid.consul:consul-api@1.4.2
    - org.jetbrains.kotlinx:kotlinx-coroutines-core@1.4.3
    - org.jetbrains.kotlinx:kotlinx-coroutines-core-jvm@1.4.3
    - com.alipay.sofa:bolt@1.6.2
    - org.lz4:lz4-java@1.7.1
    - com.ctrip.framework.apollo:apollo-client@2.0.1
    - com.ctrip.framework.apollo:apollo-core@2.0.1
    - net.jodah:failsafe@2.3.3
    - com.google.errorprone:error_prone_annotations@2.3.4
    - org.codehaus.groovy:groovy-all@2.4.4
    - org.apache.kafka:kafka-clients@2.7.2
    - org.apache.commons:commons-dbcp2@2.8.0
    - com.google.code.gson:gson@2.8.9
    - org.apache.commons:commons-pool2@2.9.0
    - com.github.ben-manes.caffeine:caffeine@2.9.3
    - com.google.code.findbugs:jsr305@3.0.2
    - org.apache.zookeeper:zookeeper@3.5.9
    - org.apache.zookeeper:zookeeper-jute@3.5.9
    - com.zaxxer:HikariCP@4.0.3
    - org.apache.httpcomponents:httpasyncclient@4.1.5
    - com.google.inject:guice@5.0.1
    - org.springframework.security:spring-security-config@5.5.6
    - org.springframework.security:spring-security-core@5.5.6
    - org.springframework.security:spring-security-crypto@5.5.6
    - org.springframework.security:spring-security-web@5.5.6
    - com.alipay.sofa:registry-client-all@6.3.0
    - com.dameng:DmJdbcDriver18@8.1.2.192
    - io.prometheus:simpleclient@0.10.0
    - io.prometheus:simpleclient_common@0.10.0
    - io.jsonwebtoken:jjwt-impl@0.10.5
    - io.jsonwebtoken:jjwt-jackson@0.10.5
    - io.perfmark:perfmark-api@0.19.0
    - com.alipay.sofa.common:sofa-common-tools@1.0.12
    - com.google.api.grpc:proto-google-common-protos@1.17.0
    - com.alibaba:fastjson@1.2.83
    - io.grpc:grpc-api@1.27.1
    - io.grpc:grpc-context@1.27.1
    - io.grpc:grpc-core@1.27.1
    - io.grpc:grpc-grpclb@1.27.1
    - io.grpc:grpc-netty@1.27.1
    - io.grpc:grpc-protobuf@1.27.1
    - io.grpc:grpc-protobuf-lite@1.27.1
    - io.grpc:grpc-stub@1.27.1
    - org.jetbrains.kotlin:kotlin-stdlib@1.4.32
    - org.jetbrains.kotlin:kotlin-stdlib-common@1.4.32
    - org.jetbrains.kotlin:kotlin-stdlib-jdk7@1.4.32
    - org.jetbrains.kotlin:kotlin-stdlib-jdk8@1.4.32
    - com.beust:jcommander@1.82
    - com.google.errorprone:error_prone_annotations@2.10.0
    - com.fasterxml.jackson.core:jackson-annotations@2.12.6
    - com.fasterxml.jackson.core:jackson-core@2.12.6
    - com.fasterxml.jackson.datatype:jackson-datatype-jdk8@2.12.6
    - com.fasterxml.jackson.module:jackson-module-parameter-names@2.12.6
    - org.apache.logging.log4j:log4j-api@2.17.2
    - org.springframework.boot:spring-boot@2.5.13
    - org.springframework.boot:spring-boot-autoconfigure@2.5.13
    - org.springframework.boot:spring-boot-configuration-processor@2.5.13
    - org.springframework.boot:spring-boot-starter@2.5.13
    - org.springframework.boot:spring-boot-starter-json@2.5.13
    - org.springframework.boot:spring-boot-starter-logging@2.5.13
    - org.springframework.boot:spring-boot-starter-security@2.5.13
    - org.springframework.boot:spring-boot-starter-tomcat@2.5.13
    - org.springframework.boot:spring-boot-starter-web@2.5.13
    - org.apache.httpcomponents:httpcore-nio@4.4.15
    - org.apache.httpcomponents:httpcore@4.4.16
    - org.apache.httpcomponents:httpclient@4.5.14
    - org.apache.tomcat.embed:tomcat-embed-el@9.0.62
    - org.apache.tomcat.embed:tomcat-embed-websocket@9.0.62
    - com.netflix.servo:servo-core@0.12.21
    - org.xerial.snappy:snappy-java@1.1.7.7
    - com.netflix.eureka:eureka-client@1.10.17
    - com.google.android:annotations@4.1.1.4
    - com.fasterxml.jackson.core:jackson-databind@2.12.6.1
    - com.google.guava:guava@30.1-jre
    - com.github.danielwegener:logback-kafka-appender@0.2.0-RC2
    - io.jsonwebtoken:jjwt-api@0.10.5
    - io.netty:netty-all@4.1.76.Final
    - io.netty:netty-buffer@4.1.76.Final
    - io.netty:netty-codec@4.1.76.Final
    - io.netty:netty-codec-dns@4.1.76.Final
    - io.netty:netty-codec-haproxy@4.1.76.Final
    - io.netty:netty-codec-http@4.1.76.Final
    - io.netty:netty-codec-http2@4.1.76.Final
    - io.netty:netty-codec-memcache@4.1.76.Final
    - io.netty:netty-codec-mqtt@4.1.76.Final
    - io.netty:netty-codec-redis@4.1.76.Final
    - io.netty:netty-codec-smtp@4.1.76.Final
    - io.netty:netty-codec-socks@4.1.76.Final
    - io.netty:netty-codec-stomp@4.1.76.Final
    - io.netty:netty-codec-xml@4.1.76.Final
    - io.netty:netty-common@4.1.76.Final
    - io.netty:netty-handler@4.1.76.Final
    - io.netty:netty-handler-proxy@4.1.76.Final
    - io.netty:netty-resolver@4.1.76.Final
    - io.netty:netty-resolver-dns@4.1.76.Final
    - io.netty:netty-resolver-dns-classes-macos@4.1.76.Final
    - io.netty:netty-resolver-dns-native-macos@4.1.76.Final
    - io.netty:netty-transport@4.1.76.Final
    - io.netty:netty-transport-classes-epoll@4.1.76.Final
    - io.netty:netty-transport-classes-kqueue@4.1.76.Final
    - io.netty:netty-transport-native-epoll@4.1.76.Final
    - io.netty:netty-transport-native-kqueue@4.1.76.Final
    - io.netty:netty-transport-native-unix-common@4.1.76.Final
    - io.netty:netty-transport-rxtx@4.1.76.Final
    - io.netty:netty-transport-sctp@4.1.76.Final
    - io.netty:netty-transport-udt@4.1.76.Final
    - io.netty:netty-handler-ssl-ocsp@4.1.86.Final
    - org.apache.tomcat.embed:tomcat-embed-core@9.0.62
    - org.springframework:spring-aop@5.3.20
    - org.springframework:spring-beans@5.3.20
    - org.springframework:spring-context@5.3.20
    - org.springframework:spring-context-support@5.3.20
    - org.springframework:spring-core@5.3.20
    - org.springframework:spring-expression@5.3.20
    - org.springframework:spring-jcl@5.3.20
    - org.springframework:spring-jdbc@5.3.20
    - org.springframework:spring-tx@5.3.20
    - org.springframework:spring-web@5.3.20
    - org.springframework:spring-webmvc@5.3.20
    - org.apache.commons:commons-math@2.2
    - org.hibernate:hibernate-validator@5.3.6.Final
    - com.github.rholder:guava-retrying@2.0.0
    - de.ruedigermoeller:fst@2.57
    - com.dyuproject.protostuff:protostuff-api@1.0.7
    - com.dyuproject.protostuff:protostuff-collectionschema@1.0.7
    - com.dyuproject.protostuff:protostuff-core@1.0.7
    - com.dyuproject.protostuff:protostuff-runtime@1.0.7
    - com.alipay.sofa:sofa-rpc-all@5.5.3
    - com.alipay.sofa:registry-store-jdbc@6.3.0
    - com.google.guava:listenablefuture@9999.0-empty-to-avoid-conflict-with-guava
    - com.vaadin.external.google:android-json@0.0.20131108.vaadin1
    - io.prometheus:simpleclient_dropwizard@0.10.0
    - io.prometheus:simpleclient_hotspot@0.10.0
    - io.etcd:jetcd-launcher@0.5.0
    - com.weibo:motan-core@1.0.0
    - com.weibo:motan-transport-netty@1.0.0
    - com.baidu:jprotobuf@1.11.11
    - io.grpc:grpc-testing@1.27.1
    - com.google.j2objc:j2objc-annotations@1.3
    - io.protostuff:protostuff-api@1.5.9
    - io.protostuff:protostuff-collectionschema@1.5.9
    - com.squareup:javapoet@1.8.0
    - com.alipay.sofa:tracer-core@2.1.2
    - com.baidu:brpc-java@2.5.9
    - com.codahale.metrics:metrics-core@3.0.1
    - com.squareup:protoparser@3.1.5
    - commons-collections:commons-collections@3.2.2
    - io.dropwizard.metrics:metrics-core@4.1.31
    - com.alipay.sofa:registry-remoting-http@6.3.0
    - com.alipay.sofa:registry-server-data@6.3.0
    - com.alipay.sofa:registry-server-integration@6.3.0
    - com.alipay.sofa:registry-server-meta@6.3.0
    - com.alipay.sofa:registry-server-session@6.3.0
    - com.alipay.sofa:registry-server-shared@6.3.0
    - com.alipay.sofa:registry-store-common@6.3.0
    - com.alipay.sofa:registry-store-jraft@6.3.0
    - com.alipay.sofa:registry-store-jraft@6.3.0
    - com.alipay.sofa:registry-test@6.3.0
    - com.alibaba.hsf:LightApi@1.0.0
    - org.opentest4j:opentest4j@1.2.0
    - org.skyscreamer:jsonassert@1.5.0
    - org.mybatis:mybatis-spring@2.0.6
    - org.jctools:jctools-core@2.1.1
    - org.jboss.resteasy:jaxrs-api@3.0.12.Final
    - org.jboss.resteasy:resteasy-client@3.0.12.Final
    - org.jboss.resteasy:resteasy-jackson-provider@3.0.12.Final
    - org.jboss.resteasy:resteasy-jaxrs@3.0.12.Final
    - org.jboss.resteasy:resteasy-netty4@3.0.12.Final
    - org.jboss.netty:netty@3.2.5.Final
    - org.jboss.logging:jboss-logging@3.4.3.Final
    - org.mybatis:mybatis@3.5.9
    - net.logstash.logback:logstash-logback-encoder@6.5
    - io.opentracing:opentracing-api@0.22.0
    - io.opentracing:opentracing-mock@0.22.0
    - io.opentracing:opentracing-noop@0.22.0
    - io.opentracing:opentracing-util@0.22.0
    - io.opencensus:opencensus-api@0.24.0
    - com.alibaba.spring:spring-context-support@1.0.2
    - org.apiguardian:apiguardian-api@1.1.2
    - org.apache.ant:ant@1.10.12
    - org.apache.ant:ant-launcher@1.10.12
    - net.bytebuddy:byte-buddy-agent@1.10.22
    - net.bytebuddy:byte-buddy@1.12.13
    - log4j:log4j@1.2.14
    - com.alipay.sofa:jraft-core@1.3.5
    - io.protostuff:protostuff-core@1.5.9
    - io.protostuff:protostuff-runtime@1.5.9
    - com.alibaba.edas:edas-sdk@1.8.3
    - org.codehaus.jackson:jackson-core-asl@1.9.12
    - org.codehaus.jackson:jackson-mapper-asl@1.9.12
    - jakarta.validation:jakarta.validation-api@2.0.2
    - org.apache.logging.log4j:log4j-jul@2.17.2
    - org.apache.logging.log4j:log4j-slf4j-impl@2.17.2
    - org.apache.logging.log4j:log4j-to-slf4j@2.17.2
    - net.jodah:failsafe@2.3.3
    - net.minidev:accessors-smart@2.4.8
    - net.minidev:json-smart@2.4.8
    - com.alibaba:dubbo@2.6.10
    - org.apache.curator:curator-test@2.9.1
    - org.assertj:assertj-core@3.12.2
    - cglib:cglib@3.2.5
    - com.alipay.sofa:hessian@4.0.3
    - org.apache.commons:commons-collections4@4.1
    - com.alipay.sofa:registry-common-model@6.3.0
    - com.alipay.sofa:registry-common-util@6.3.0
    - com.alipay.sofa:registry-core@6.3.0
    - com.alipay.sofa:registry-remoting-api@6.3.0
    - com.alipay.sofa:registry-remoting-bolt@6.3.0
    - org.apache.skywalking:apm-agent-core@8.6.0
    - com.kohlschutter.junixsocket:junixsocket-common@2.0.4
    - com.kohlschutter.junixsocket:junixsocket-native-common@2.0.4
    - com.lmax:disruptor@3.4.4
    - com.jayway.jsonpath:json-path@2.5.0
    - org.eclipse.jetty:jetty-security@9.4.38.v20210224
    - org.eclipse.jetty:jetty-servlet@9.4.38.v20210224
    - org.eclipse.jetty:jetty-http@9.4.46.v20220331
    - org.eclipse.jetty:jetty-io@9.4.46.v20220331
    - org.eclipse.jetty:jetty-server@9.4.46.v20220331
    - org.eclipse.jetty:jetty-util@9.4.46.v20220331
    - org.eclipse.jetty:jetty-util-ajax@9.4.46.v20220331
    - org.rocksdb:rocksdbjni@5.18.4
    - org.codehaus.jackson:jackson-jaxrs@1.9.12
    - org.codehaus.jackson:jackson-xc@1.9.12
    - com.github.microwww:redis-server@0.3.0
    - org.javassist:javassist@3.21.0-GA

- BSD-2-Clause
    - org.postgresql:postgresql@42.2.25
    - com.github.luben:zstd-jni@1.5.0-4

- BSD-3-Clause
    - org.antlr:antlr-runtime@3.4
    - org.antlr:ST4@4.3
    - org.antlr:antlr4@4.8
    - org.antlr:antlr-runtime@3.5.2
    - com.thoughtworks.xstream:xstream@1.4.19
    - com.esotericsoftware:minlog@1.3.1
    - com.esotericsoftware:kryo@5.4.0
    - com.esotericsoftware:reflectasm@1.11.9
    - com.google.protobuf:protobuf-java-util@3.11.0
    - com.google.protobuf:protobuf-java@3.16.3
    - org.hamcrest:hamcrest@2.2
    - org.hamcrest:hamcrest-core@2.2
    - org.codehaus.janino:commons-compiler@3.1.7
    - org.codehaus.janino:janino@3.1.7
    - com.thoughtworks.xstream:xstream@1.4.20
    - org.ow2.asm:asm@9.1
    - org.abego.treelayout:org.abego.treelayout.core@1.0.3

- BSD License
    - antlr:antlr@2.7.7
    - org.antlr:antlr4-runtime@4.8
    - org.antlr:stringtemplate@3.2.1

- CDDL-1.0
    - javax.ws.rs:jsr311-api@1.1.1
    - javax.servlet:javax.servlet-api@4.0.1

- CDDL License
    - org.glassfish:javax.json@1.0.4
    - com.sun.jersey.contribs:jersey-apache-client4@1.19.1
    - com.sun.jersey:jersey-client@1.19.1
    - com.sun.jersey:jersey-core@1.19.1
    - org.jboss.spec.javax.annotation:jboss-annotations-api_1.1_spec@1.0.1.Final

- EDL-1.0
    - jakarta.activation:jakarta.activation-api@1.2.2

- EPL1.0
    - junit:junit@4.13.2
    - ch.qos.logback:logback-classic@1.2.9
    - ch.qos.logback:logback-core@1.2.9
    - ch.qos.logback:logback-classic@1.2.11
    - ch.qos.logback:logback-core@1.2.11
    - com.h2database:h2@1.4.200

- EPL2.0
    - org.junit.platform:junit-platform-commons@1.8.2
    - org.junit.platform:junit-platform-engine@1.8.2
    - org.junit.platform:junit-platform-launcher@1.8.2
    - org.junit.jupiter:junit-jupiter@5.8.2
    - org.junit.jupiter:junit-jupiter-api@5.8.2
    - org.junit.jupiter:junit-jupiter-engine@5.8.2
    - org.junit.jupiter:junit-jupiter-params@5.8.2
    - jakarta.annotation:jakarta.annotation-api@1.3.5
    - jakarta.ws.rs:jakarta.ws.rs-api@2.1.6
    - org.glassfish.hk2:osgi-resource-locator@1.0.3
    - org.glassfish.hk2.external:aopalliance-repackaged@2.6.1
    - org.glassfish.hk2.external:jakarta.inject@2.6.1
    - org.glassfish.hk2:hk2-api@2.6.1
    - org.glassfish.hk2:hk2-locator@2.6.1
    - org.glassfish.hk2:hk2-utils@2.6.1

- MIT
    - org.codehaus.mojo:animal-sniffer-annotations@1.18
    - org.checkerframework:checker-qual@3.5.0
    - org.slf4j:jul-to-slf4j@1.7.32
    - org.slf4j:slf4j-api@1.7.32
    - org.slf4j:jul-to-slf4j@1.7.36
    - org.slf4j:slf4j-api@1.7.36
    - org.slf4j:slf4j-reload4j@1.7.36
    - org.slf4j:slf4j-simple@1.7.36
    - redis.clients:jedis@3.2.0
    - com.github.andrewoma.dexx:dexx-collections@0.2
    - org.rnorth:tcp-unix-socket-proxy@1.0.2
    - org.rnorth.duct-tape:duct-tape@1.0.7
    - org.rnorth.visible-assertions:visible-assertions@2.1.2
    - org.mockito:mockito-core@2.23.4
    - org.mockito:mockito-junit-jupiter@2.23.4

- New BSD License
    - com.googlecode.protobuf-java-format:protobuf-java-format@1.4

- PublicDomain
    - aopalliance:aopalliance@1.0

- Unicode/ICU License
    - com.ibm.icu:icu4j@61.1

- Simplified BSD License
    - org.scijava:native-lib-loader@2.4.0

- Indiana University Extreme! Lab Software License
    - io.github.x-stream:mxparser@1.2.2

- GPL-2.0 with FOSSexception
    - mysql:mysql-connector-java@8.0.28



##### seata/seata-go
https://github.com/seata/seata-go/tree/master

- Apache-2.0
    - github.com/envoyproxy/protoc-gen-validate@v0.1.0
    - github.com/google/renameio@v0.1.0
    - github.com/nats-io/nkeys@v0.1.3
    - github.com/npillmayer/nestext@v0.1.3
    - github.com/mschoch/smat@v0.2.0
    - github.com/prometheus/client_model@v0.2.0
    - github.com/census-instrumentation/opencensus-proto@v0.2.1
    - github.com/jonboulle/clockwork@v0.2.2
    - github.com/openzipkin/zipkin-go@v0.2.2
    - github.com/arana-db/parser@v0.2.5
    - github.com/coreos/go-semver@v0.3.0
    - github.com/nats-io/jwt@v0.3.2
    - github.com/oklog/oklog@v0.3.2
    - github.com/jmespath/go-jmespath@v0.4.0
    - github.com/tklauser/numcpus@v0.4.0
    - contrib.go.opencensus.io/exporter/prometheus@v0.4.1
    - github.com/openzipkin-contrib/zipkin-go-opentracing@v0.4.5
    - go.opentelemetry.io/proto/otlp@v0.7.0
    - github.com/prometheus/tsdb@v0.7.1
    - github.com/prometheus/procfs@v0.7.3
    - github.com/golang/glog@v1.0.0
    - github.com/google/btree@v1.0.0
    - github.com/google/gofuzz@v1.0.0
    - github.com/inconshreveable/mousetrap@v1.0.0
    - github.com/oklog/run@v1.0.0
    - github.com/nats-io/nuid@v1.0.1
    - github.com/modern-go/reflect2@v1.0.2
    - github.com/alibaba/sentinel-golang@v1.0.4
    - github.com/matttproud/golang_protobuf_extensions@v1.0.4
    - cloud.google.com/go/datastore@v1.1.0
    - cloud.google.com/go/firestore@v1.1.0
    - github.com/gogo/googleapis@v1.1.0
    - github.com/spf13/cobra@v1.1.1
    - github.com/spf13/afero@v1.1.2
    - github.com/nacos-group/nacos-sdk-go@v1.1.3
    - github.com/grpc-ecosystem/go-grpc-prometheus@v1.2.0
    - github.com/opentracing/opentracing-go@v1.2.0
    - github.com/OneOfOne/xxhash@v1.2.2
    - github.com/go-logr/stdr@v1.2.2
    - github.com/grpc-ecosystem/go-grpc-middleware@v1.2.2
    - github.com/go-logr/logr@v1.2.3
    - github.com/aws/aws-sdk-go-v2/internal/ini@v1.2.4
    - github.com/cockroachdb/errors@v1.2.4
    - cloud.google.com/go/pubsub@v1.3.1
    - github.com/oklog/ulid@v1.3.1
    - github.com/aws/aws-sdk-go-v2/service/internal/presigned-url@v1.3.2
    - github.com/aws/aws-sdk-go-v2/service/appconfig@v1.4.2
    - github.com/aws/aws-sdk-go-v2/service/sso@v1.4.2
    - github.com/aws/aws-sdk-go-v2/credentials@v1.4.3
    - github.com/aws/aws-sdk-go-v2/feature/ec2/imds@v1.6.0
    - github.com/golang/mock@v1.6.0
    - github.com/jhump/protoreflect@v1.6.0
    - google.golang.org/appengine@v1.6.6
    - github.com/aws/aws-sdk-go-v2/service/sts@v1.7.2
    - cloud.google.com/go/bigquery@v1.8.0
    - github.com/aws/smithy-go@v1.8.0
    - github.com/aws/aws-sdk-go-v2/config@v1.8.3
    - github.com/bytedance/sonic@v1.9.1
    - github.com/nats-io/nats.go@v1.9.1
    - github.com/aws/aws-sdk-go-v2@v1.9.2
    - github.com/casbin/casbin/v2@v2.1.2
    - github.com/nats-io/nats-server/v2@v2.1.2
    - github.com/nacos-group/nacos-sdk-go/v2@v2.2.2
    - gopkg.in/square/go-jose.v2@v2.3.1
    - gopkg.in/yaml.v2@v2.4.0
    - github.com/google/martian/v3@v3.0.0
    - dubbo.apache.org/dubbo-go/v3@v3.0.4
    - go.etcd.io/etcd/api/v3@v3.5.6
    - go.etcd.io/etcd/client/pkg/v3@v3.5.6
    - go.etcd.io/etcd/client/v3@v3.5.6
    - github.com/lyft/protoc-gen-validate@v0.0.13
    - github.com/apache/thrift@v0.13.0
    - github.com/prometheus/statsd_exporter@v0.21.0
    - go.opencensus.io@v0.23.0
    - github.com/prometheus/common@v0.32.1
    - cloud.google.com/go@v0.65.0
    - github.com/Workiva/go-datastructures@v1.0.52
    - cloud.google.com/go/storage@v1.10.0
    - go.opentelemetry.io/otel@v1.11.0
    - go.opentelemetry.io/otel/trace@v1.11.0
    - github.com/apache/dubbo-go-hessian2@v1.11.4
    - github.com/prometheus/client_golang@v1.12.2
    - github.com/aws/aws-lambda-go@v1.13.3
    - github.com/dubbogo/gost@v1.14.0
    - github.com/aws/aws-sdk-go@v1.27.0
    - google.golang.org/grpc@v1.51.0
    - gopkg.in/ini.v1@v1.66.2
    - github.com/coreos/go-systemd/v22@v22.3.2
    - github.com/dubbogo/grpc-go@v1.42.10
    - github.com/dubbogo/triple@v1.2.2-rc2
    - github.com/aliyun/alibaba-cloud-sdk-go@v1.61.1704
    - go.etcd.io/etcd/pkg/v3@v3.5.0-alpha.0
    - go.etcd.io/etcd/raft/v3@v3.5.0-alpha.0
    - go.etcd.io/etcd/server/v3@v3.5.0-alpha.0
    - go.etcd.io/etcd/client/v2@v2.305.0-alpha.0
    - github.com/google/martian@v2.1.0+incompatible
    - gotest.tools@v2.2.0+incompatible
    - github.com/uber/jaeger-lib@v2.4.1+incompatible
    - github.com/uber/jaeger-client-go@v2.30.0+incompatible
    - github.com/coreos/etcd@v3.3.13+incompatible
    - github.com/opentracing-contrib/go-observer@v0.0.0-20170622124052-a52f23424492
    - github.com/modern-go/concurrent@v0.0.0-20180306012644-bacd9c7ef1dd
    - github.com/coreos/pkg@v0.0.0-20180928190104-399ea9e2e55f
    - github.com/coreos/go-systemd@v0.0.0-20190321100706-95778dfbb74e
    - github.com/cockroachdb/logtags@v0.0.0-20190617123548-eb05cc24525f
    - github.com/mwitkow/go-conntrack@v0.0.0-20190716064945-2f068394615f
    - go.etcd.io/etcd@v0.0.0-20191023171146-3cf2f69b5738
    - github.com/google/pprof@v0.0.0-20200708004538-1a94d8640e99
    - github.com/cockroachdb/datadriven@v0.0.0-20200714090401-bf6692d28da5
    - github.com/golang/groupcache@v0.0.0-20210331224755-41bb18bfe9da
    - github.com/pingcap/log@v0.0.0-20210906054005-afc726e70354
    - github.com/cncf/udpa/go@v0.0.0-20210930031921-04548b0d99d4
    - github.com/cncf/xds/go@v0.0.0-20211011173535-cb28da3451f1
    - google.golang.org/genproto@v0.0.0-20220630174209-ad1d48641aa7
    - github.com/chenzhuoyu/base64x@v0.0.0-20221115062448-fe3a3abad311
    - github.com/soheilhy/cmux@v0.1.5-0.20210205191134-5ec6847320e5
    - github.com/envoyproxy/go-control-plane@v0.10.2-0.20220325020618-49ff273808a1
    - github.com/apache/dubbo-getty@v1.4.10-0.20230731065302-7c0f0039e59c
    - github.com/pelletier/go-toml@v1.9.3
    - gopkg.in/yaml.v3@v3.0.1
    - github.com/RoaringBitmap/roaring@v1.2.0
    - github.com/klauspost/compress@v1.15.11

- BSD-2-Clause
    - gopkg.in/warnings.v0@v0.1.2
    - github.com/rhnvrm/simples3@v0.6.1
    - github.com/pkg/errors@v0.9.1
    - github.com/pkg/profile@v1.2.1
    - github.com/gorilla/websocket@v1.4.2
    - github.com/magiconair/properties@v1.8.6
    - github.com/russross/blackfriday/v2@v2.0.1
    - github.com/godbus/dbus/v5@v5.0.4
    - github.com/streadway/amqp@v0.0.0-20190827072141-edfb9018d271
    - github.com/gopherjs/gopherjs@v0.0.0-20190910122728-9d188e94fb99
    - gopkg.in/check.v1@v1.0.0-20201130134442-10cb98267c6c
    - github.com/pingcap/errors@v0.11.5-0.20210425183316-da1aaba5fb63
    - github.com/streadway/handy@v0.0.0-20190108123426-d5acb3125c2a

- BSD-2-Clause-Views
    - github.com/rcrowley/go-metrics@v0.0.0-20181016184325-3113b8401b8a

- BSD-3-Clause
    - github.com/dsnet/compress@v0.0.1
    - github.com/hashicorp/go.net@v0.0.1
    - github.com/dubbogo/net@v0.0.4
    - github.com/golang/snappy@v0.0.4
    - golang.org/x/sync@v0.1.0
    - rsc.io/pdf@v0.1.1
    - github.com/circonus-labs/circonusllhist@v0.1.3
    - github.com/getsentry/raven-go@v0.2.0
    - rsc.io/binaryregexp@v0.2.0
    - golang.org/x/arch@v0.3.0
    - github.com/hashicorp/go-msgpack@v0.5.3
    - github.com/ulikunitz/xz@v0.5.6
    - github.com/google/go-cmp@v0.5.9
    - golang.org/x/tools@v0.6.0
    - golang.org/x/mod@v0.8.0
    - golang.org/x/sys@v0.8.0
    - golang.org/x/term@v0.8.0
    - gonum.org/v1/gonum@v0.8.2
    - golang.org/x/crypto@v0.9.0
    - golang.org/x/text@v0.9.0
    - github.com/edsrzf/mmap-go@v1.0.0
    - github.com/pmezard/go-difflib@v1.0.0
    - modernc.org/fileutil@v1.0.0
    - modernc.org/lex@v1.0.0
    - modernc.org/lexer@v1.0.0
    - modernc.org/sortutil@v1.0.0
    - modernc.org/golex@v1.0.1
    - modernc.org/y@v1.0.1
    - github.com/spf13/pflag@v1.0.5
    - github.com/spaolacci/murmur3@v1.1.0
    - modernc.org/strutil@v1.1.0
    - github.com/gorilla/context@v1.1.1
    - github.com/bits-and-blooms/bitset@v1.2.0
    - github.com/pborman/uuid@v1.2.0
    - github.com/rogpeppe/fastuuid@v1.2.0
    - gopkg.in/gcfg.v1@v1.2.3
    - github.com/google/uuid@v1.3.0
    - github.com/julienschmidt/httprouter@v1.3.0
    - rsc.io/sampler@v1.3.0
    - github.com/gogo/protobuf@v1.3.2
    - github.com/jessevdk/go-flags@v1.4.0
    - modernc.org/mathutil@v1.4.1
    - gopkg.in/fsnotify.v1@v1.4.7
    - github.com/DATA-DOG/go-sqlmock@v1.5.0
    - github.com/golang/protobuf@v1.5.2
    - github.com/fsnotify/fsnotify@v1.6.0
    - github.com/gorilla/mux@v1.7.3
    - github.com/rogpeppe/go-internal@v1.8.0
    - github.com/googleapis/gax-go/v2@v2.0.5
    - gopkg.in/errgo.v2@v2.1.0
    - rsc.io/quote/v3@v3.1.0
    - github.com/evanphx/json-patch/v5@v5.5.0
    - golang.org/x/net@v0.10.0
    - github.com/twitchyliquid64/golang-asm@v0.15.1
    - github.com/tklauser/go-sysconf@v0.3.10
    - google.golang.org/api@v0.30.0
    - gopkg.in/cheggaaa/pb.v1@v1.0.25
    - github.com/miekg/dns@v1.1.41
    - github.com/grpc-ecosystem/grpc-gateway@v1.16.0
    - google.golang.org/protobuf@v1.30.0
    - github.com/shirou/gopsutil/v3@v3.22.2
    - github.com/pierrec/lz4/v4@v4.1.17
    - github.com/circonus-labs/circonus-gometrics@v2.3.1+incompatible
    - github.com/pierrec/lz4@v2.5.2+incompatible
    - github.com/op/go-logging@v0.0.0-20160315200505-970db520ece7
    - github.com/cznic/strutil@v0.0.0-20171016134553-529a34b1c186
    - github.com/dsnet/golib@v0.0.0-20171103203638-1ea166775780
    - github.com/grpc-ecosystem/grpc-opentracing@v0.0.0-20180507213350-8e809c8a8645
    - github.com/ianlancetaylor/demangle@v0.0.0-20181102032728-5e5cf60278f6
    - github.com/cznic/sortutil@v0.0.0-20181122101858-f5f958428db8
    - github.com/cznic/mathutil@v0.0.0-20181122101859-297441e03548
    - gonum.org/v1/netlib@v0.0.0-20190313105609-8cb42192e0e0
    - dmitri.shuralyov.com/gpu/mtl@v0.0.0-20190408044501-666a987793e9
    - github.com/go-gl/glfw@v0.0.0-20190409004039-e6da0acd62b1
    - github.com/alecthomas/template@v0.0.0-20190718012654-fb15b899a751
    - golang.org/x/mobile@v0.0.0-20190719004257-d2bd2a29d028
    - golang.org/x/image@v0.0.0-20190802002840-cff245a6509b
    - github.com/samuel/go-zookeeper@v0.0.0-20190923202752-2cc03de413da
    - github.com/clbanning/x2j@v0.0.0-20191024224557-825249438eec
    - github.com/go-gl/glfw/v3.3/glfw@v0.0.0-20200222043503-6f7a984d4dc4
    - golang.org/x/exp@v0.0.0-20200331195152-e8c3332aa8e5
    - github.com/remyoudompheng/bigfft@v0.0.0-20200410134404-eec4a21b6bb0
    - golang.org/x/xerrors@v0.0.0-20200804184101-5ec99f83aff1
    - github.com/pkg/diff@v0.0.0-20210226163009-20ebb0f2a09e
    - golang.org/x/lint@v0.0.0-20210508222113-6edffad5e616
    - github.com/lufia/plan9stats@v0.0.0-20211012122336-39d0f177ccd0
    - golang.org/x/oauth2@v0.0.0-20211104180415-d3ed0bb246c8
    - golang.org/x/time@v0.0.0-20220722155302-e5dcc9cfc0b9
    - gopkg.in/tomb.v1@v1.0.0-20141024135613-dd632973f1e7
    - github.com/dubbogo/go-zookeeper@v1.0.4-0.20211212162352-f9d2183d89d5
    - github.com/BurntSushi/xgb@v0.0.0-20160522181843-27f122750802
    - modernc.org/scanner@v1.0.1
    - modernc.org/parser@v1.0.2
    - gonum.org/v1/plot@v0.0.0-20190515093506-e2840ee46a6b

- CC0-1.0
    - github.com/pascaldekloe/goe@v0.1.0

- CCPL-4.0
    - github.com/ajstarks/svgo@v0.0.0-20180226025133-644b8db467af

- FreeType License
    - github.com/golang/freetype@v0.0.0-20170609003504-e2365dfdc4a0

- ISC
    - github.com/davecgh/go-spew@v1.1.1
    - vimagination.zapto.org/byteio@v0.0.0-20200222190125-d27cba0f0b10
    - vimagination.zapto.org/memio@v0.0.0-20200222190306-588ebc67b97d

- MIT
    - github.com/bluele/gcache@v0.0.2
    - github.com/mattn/go-runewidth@v0.0.2
    - github.com/bgentry/speakeasy@v0.1.0
    - github.com/gin-contrib/sse@v0.1.0
    - github.com/go-kit/log@v0.1.0
    - github.com/mattn/go-colorable@v0.1.8
    - github.com/kr/text@v0.2.0
    - github.com/kr/pretty@v0.3.0
    - github.com/client9/misspell@v0.3.4
    - github.com/jinzhu/copier@v0.3.5
    - github.com/armon/go-metrics@v0.3.9
    - github.com/sony/gobreaker@v0.4.1
    - github.com/go-logfmt/logfmt@v0.5.0
    - github.com/stretchr/objx@v0.5.0
    - github.com/montanaflynn/stats@v0.6.6
    - github.com/jstemmer/go-junit-report@v0.9.1
    - github.com/VividCortex/gohistogram@v1.0.0
    - github.com/antihax/optional@v1.0.0
    - github.com/armon/go-radix@v1.0.0
    - github.com/dustin/go-humanize@v1.0.0
    - github.com/fatih/camelcase@v1.0.0
    - github.com/hashicorp/go-syslog@v1.0.0
    - github.com/hpcloud/tail@v1.0.0
    - github.com/jpillora/backoff@v1.0.0
    - github.com/kisielk/gotool@v1.0.0
    - github.com/mitchellh/go-testing-interface@v1.0.0
    - github.com/mitchellh/go-wordwrap@v1.0.0
    - github.com/mitchellh/iochan@v1.0.0
    - github.com/opentracing/basictracer-go@v1.0.0
    - github.com/ryanuber/go-glob@v1.0.0
    - github.com/shurcooL/sanitized_anchor_name@v1.0.0
    - github.com/spf13/jwalterweatherman@v1.0.0
    - github.com/beorn7/perks@v1.0.1
    - github.com/go-errors/errors@v1.0.1
    - github.com/go-test/deep@v1.0.2
    - github.com/mitchellh/reflectwalk@v1.0.2
    - github.com/konsorten/go-windows-terminal-sequences@v1.0.3
    - github.com/hashicorp/mdns@v1.0.4
    - github.com/pact-foundation/pact-go@v1.0.4
    - github.com/BurntSushi/toml@v1.1.0
    - github.com/benbjohnson/clock@v1.1.0
    - github.com/cespare/xxhash@v1.1.0
    - github.com/eapache/go-resiliency@v1.1.0
    - github.com/eapache/queue@v1.1.0
    - github.com/fatih/structs@v1.1.0
    - github.com/mitchellh/go-homedir@v1.1.0
    - github.com/buger/jsonparser@v1.1.1
    - github.com/kr/pty@v1.1.1
    - github.com/HdrHistogram/hdrhistogram-go@v1.1.2
    - github.com/klauspost/cpuid@v1.2.0
    - github.com/mitchellh/copystructure@v1.2.0
    - github.com/subosito/gotenv@v1.2.0
    - github.com/yusufpapurcu/wmi@v1.2.2
    - github.com/posener/complete@v1.2.3
    - github.com/leodido/go-urn@v1.2.4
    - github.com/go-ole/go-ole@v1.2.6
    - github.com/ugorji/go@v1.2.6
    - github.com/hudl/fargo@v1.3.0
    - github.com/joho/godotenv@v1.3.0
    - github.com/spf13/cast@v1.3.0
    - github.com/go-asn1-ber/asn1-ber@v1.3.1
    - github.com/coreos/bbolt@v1.3.2
    - go.etcd.io/bbolt@v1.3.5
    - github.com/gabriel-vasile/mimetype@v1.4.2
    - github.com/onsi/gomega@v1.4.3
    - github.com/knadh/koanf@v1.4.4
    - github.com/kisielk/errcheck@v1.5.0
    - github.com/mitchellh/mapstructure@v1.5.0
    - github.com/jmespath/go-jmespath/internal/testify@v1.5.1
    - github.com/creasty/defaults@v1.5.2
    - github.com/smartystreets/goconvey@v1.6.4
    - github.com/onsi/ginkgo@v1.7.0
    - github.com/sirupsen/logrus@v1.7.0
    - github.com/spf13/viper@v1.7.0
    - github.com/go-stack/stack@v1.8.0
    - go.uber.org/multierr@v1.8.0
    - github.com/stretchr/testify@v1.8.3
    - github.com/fatih/color@v1.9.0
    - github.com/go-co-op/gocron@v1.9.0
    - go.uber.org/atomic@v1.9.0
    - github.com/gin-gonic/gin@v1.9.1
    - github.com/cpuguy83/go-md2man/v2@v2.0.0
    - gopkg.in/natefinch/lumberjack.v2@v2.0.0
    - github.com/pelletier/go-toml/v2@v2.0.8
    - github.com/cespare/xxhash/v2@v2.1.2
    - github.com/go-playground/assert/v2@v2.2.0
    - github.com/klauspost/cpuid/v2@v2.2.4
    - gopkg.in/alecthomas/kingpin.v2@v2.2.6
    - github.com/go-resty/resty/v2@v2.7.0
    - github.com/agiledragon/gomonkey/v2@v2.9.0
    - github.com/robfig/cron/v3@v3.0.1
    - github.com/hjson/hjson-go/v4@v4.0.0
    - github.com/mattn/go-isatty@v0.0.19
    - github.com/go-kit/kit@v0.10.0
    - github.com/goccy/go-json@v0.10.2
    - github.com/go-playground/locales@v0.14.1
    - github.com/hashicorp/go-hclog@v0.16.2
    - github.com/go-playground/universal-translator@v0.18.1
    - github.com/lightstep/lightstep-tracer-go@v0.18.1
    - github.com/chzyer/logex@v1.1.10
    - github.com/creack/pty@v1.1.11
    - go.uber.org/goleak@v1.1.11
    - github.com/json-iterator/go@v1.1.12
    - github.com/frankban/quicktest@v1.10.0
    - gopkg.in/resty.v1@v1.12.0
    - github.com/Shopify/sarama@v1.19.0
    - github.com/ugorji/go/codec@v1.2.11
    - go.uber.org/zap@v1.21.0
    - github.com/urfave/cli@v1.22.1
    - github.com/yuin/goldmark@v1.4.13
    - github.com/sijms/go-ora/v2@v2.5.17
    - github.com/go-ldap/ldap/v3@v3.1.10
    - github.com/emicklei/go-restful/v3@v3.10.1
    - github.com/go-playground/validator/v10@v10.14.0
    - honnef.co/go/tools@v0.0.1-2020.1.4
    - github.com/natefinch/lumberjack@v2.0.0+incompatible
    - github.com/agiledragon/gomonkey@v2.0.2+incompatible
    - github.com/ryanuber/columnize@v2.1.0+incompatible
    - github.com/Shopify/toxiproxy@v2.1.4+incompatible
    - github.com/cenkalti/backoff@v2.2.1+incompatible
    - github.com/performancecopilot/speed@v3.0.0+incompatible
    - github.com/k0kubun/pp@v3.0.1+incompatible
    - github.com/go-ldap/ldap@v3.0.2+incompatible
    - github.com/DataDog/datadog-go@v3.2.0+incompatible
    - github.com/dgrijalva/jwt-go@v3.2.0+incompatible
    - github.com/form3tech-oss/jwt-go@v3.2.2+incompatible
    - github.com/jtolds/gls@v4.20.0+incompatible
    - github.com/kr/logfmt@v0.0.0-20140226030751-b84e30acd515
    - github.com/k0kubun/colorstring@v0.0.0-20150214042306-9440f1994b88
    - github.com/tv42/httpunix@v0.0.0-20150427012821-b75d8614f926
    - github.com/armon/circbuf@v0.0.0-20150827004946-bbbad097214e
    - github.com/goji/httpauth@v0.0.0-20160601135302-2da839ab0f4d
    - github.com/codahale/hdrhistogram@v0.0.0-20161010025455-3a0bb77429bd
    - github.com/olekukonko/tablewriter@v0.0.0-20170122224234-a0225b3f23b5
    - github.com/aryann/difflib@v0.0.0-20170710044230-e206f873d14a
    - github.com/koding/multiconfig@v0.0.0-20171124222453-69c27309b2d7
    - github.com/franela/goreq@v0.0.0-20171204163338-bcd34c9993f8
    - github.com/chzyer/test@v0.0.0-20180213035817-a1ea475d72b1
    - github.com/afex/hystrix-go@v0.0.0-20180502004556-fa1af6a1f4f5
    - github.com/chzyer/readline@v0.0.0-20180603132655-2972be24d48e
    - github.com/oliveagle/jsonpath@v0.0.0-20180606110733-2e52cf6e6852
    - github.com/eapache/go-xerial-snappy@v0.0.0-20180814174437-776d5712da21
    - github.com/smartystreets/assertions@v0.0.0-20180927180507-b2de0cb4f26d
    - github.com/dgryski/go-sip13@v0.0.0-20181026042036-e10d5fee7954
    - github.com/xiang90/probing@v0.0.0-20190116061207-43a291ad63a2
    - github.com/StackExchange/wmi@v0.0.0-20190523213315-cbe66965904d
    - github.com/lightstep/lightstep-tracer-common/golang/gogo@v0.0.0-20190605223551-bc2310a04743
    - go.uber.org/tools@v0.0.0-20190618225709-2cfd321de3ee
    - sourcegraph.com/sourcegraph/appdash@v0.0.0-20190731080439-ebfcffb1b5c0
    - github.com/alecthomas/units@v0.0.0-20190924025748-f65c72e2690d
    - github.com/influxdata/influxdb1-client@v0.0.0-20191209144304-8bf82d3c094d
    - github.com/franela/goblin@v0.0.0-20200105215937-c9ffbefa60db
    - github.com/niemeyer/pretty@v0.0.0-20200227124842-a10e7caefd8e
    - github.com/tmc/grpc-websocket-proxy@v0.0.0-20201229170055-e5319fda7802
    - github.com/power-devops/perfstat@v0.0.0-20210106213030-5aafc221ea8c
    - gopkg.in/asn1-ber.v1@v1.0.0-20181015200546-f715ec2f112d
    - github.com/bketelsen/crypt@v0.0.3-0.20200106085610-5cbc8cc4026c
    - github.com/jung-kurt/gofpdf@v1.0.3-0.20190309125859-24315acbbda5
    - github.com/satori/go.uuid@v1.2.1-0.20181028125025-b2ce2384e17b
    - github.com/fogleman/gg@v1.2.1-0.20190220221249-0403632d5b90
    - github.com/Knetic/govaluate@v3.0.1-0.20171022003610-9aa49832a739+incompatible
    - github.com/ghodss/yaml@v1.0.0
    - sigs.k8s.io/yaml@v1.2.0
    - github.com/sean-/seed@v0.0.0-20170313163322-e2103e2c3529

- MPL-2.0
    - github.com/hashicorp/go-secure-stdlib/base62@v0.1.1
    - github.com/hashicorp/go-secure-stdlib/mlock@v0.1.1
    - github.com/hashicorp/go-secure-stdlib/password@v0.1.1
    - github.com/hashicorp/go-secure-stdlib/tlsutil@v0.1.1
    - github.com/hashicorp/go-secure-stdlib/strutil@v0.1.2
    - github.com/hashicorp/go-secure-stdlib/parseutil@v0.1.6
    - github.com/hashicorp/memberlist@v0.3.0
    - github.com/mitchellh/gox@v0.4.0
    - github.com/hashicorp/go-cleanhttp@v0.5.1
    - github.com/hashicorp/go-retryablehttp@v0.5.4
    - github.com/hashicorp/golang-lru@v0.5.4
    - github.com/hashicorp/vault/sdk@v0.6.0
    - github.com/hashicorp/consul/sdk@v0.8.0
    - github.com/hashicorp/serf@v0.9.6
    - github.com/hashicorp/hcl@v1.0.0
    - github.com/hashicorp/logutils@v1.0.0
    - github.com/hashicorp/go-rootcerts@v1.0.2
    - github.com/hashicorp/go-sockaddr@v1.0.2
    - github.com/hashicorp/go-uuid@v1.0.2
    - github.com/hashicorp/vault/api@v1.0.4
    - github.com/hashicorp/errwrap@v1.1.0
    - github.com/mitchellh/cli@v1.1.0
    - github.com/hashicorp/go-multierror@v1.1.1
    - github.com/hashicorp/go-version@v1.2.0
    - github.com/hashicorp/go-immutable-radix@v1.3.1
    - github.com/hashicorp/go-plugin@v1.4.3
    - github.com/go-sql-driver/mysql@v1.6.0
    - github.com/hashicorp/go-kms-wrapping/entropy/v2@v2.0.0
    - github.com/hashicorp/consul/api@v1.13.0
    - github.com/hashicorp/yamux@v0.0.0-20181012175058-2f1d1f20f75d
    - github.com/certifi/gocertifi@v0.0.0-20191021191039-0944d244cd40

_The above dependencies and licenses have all been manually confirmed, using [skywalking-eyes](https://github.com/apache/skywalking-eyes) checks in the process._


### Required Resources
#### Git Repositories
#### Issue Tracking
The community would like to continue using [GitHub](https://github.com/seata/seata/issues) Issues.
#### Continuous Integration tool
Github Actions Plugin Market

#### Mailing Lists
seata-dev: for development discussions
seata-private: for PPMC discussions
seata-notifications: for users notifications, and notifications from GitHub
#### Initial Committers
- Min Ji (GitHub ID = slievrly) [slievrly@gmail.com]
- Albumen Kevin(GitHub ID = AlbumenJ) [albumenj@apache.org]
- Te Wang (GitHub ID = wt-better) [m18091785089@163.com]
- Jianbin Chen (GitHub ID = funky-eyes) [364176773@qq.com]
- Liang Wang (GitHub ID = wangliang181230) [841369634@qq.com]
- Jiangke Wu (GitHub ID = xingfudeshi) [xingfudeshi@gmail.com]
- Yuecai Liu（GitHub ID = luky116）[luky116@apache.org]
- Yanlin Li（GitHub ID = yanlinly）[yan.lin2009@163.com]
- Haiqiang Shen（GitHub ID = sharajava）[sharajava@gmail.com]
- Jiawei Zhang (GitHub ID = l81893521) [349071347@qq.com]
- Zhengtao Zhong (GitHub ID = jsbxyyx) [jsbxyyx@163.com]
- Xin Wang (GitHub ID = lovepoem) [wangxin@apache.org]
- Jinlei Zhuang（GitHub ID = zjinlei）[75718677@qq.com]

#### Affiliations
- Alibaba: Min Ji, Albumen Kevin, Yanlin Li, Haiqiang Shen
- Ant Group: Te Wang
- TongDun: Jianbin Chen
- EWorld: Liang Wang
- 360: Yuecai Liu
- TruthAI: Jiangke Wu
- DaShenLin: Jiawei Zhang
- JD: Xin Wang
- Helios: Jinlei Zhuang
- Individual Developer: Zhengtao Zhong
### Sponsors
#### Champion
- Sheng Wu(wusheng at apache dot org)
#### Mentors
- Sheng Wu(wusheng at apache dot org)
- Justin Mclean(justin at classsoftware dot com)
- Huxing Zhang(huxing at apache dot org)
- Heng Du(duhengforever at apache dot org)

#### Sponsoring Entity
We are expecting the Apache Incubator could sponsor this project.