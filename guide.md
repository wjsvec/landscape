> 云原生景观图指南由 ]CNCF 商业价值小组委员会](https://github.com/cncf/business-value) 
> 和 [Cartografos 团队](https://github.com/cncf/cartografos)发起。
> 本指南由 [Jason Morgan](https://www.linkedin.com/in/jasonmorgan2/) 
> 和 [Catherine Paganini](https://www.linkedin.com/in/catherinepaganini/) 撰写，
> 由 [Simon Forster](https://www.linkedin.com/in/forsters/) 
> 和 [Ihor Dvoretskyi](https://www.linkedin.com/in/idvoretskyi/) 编辑和审查，
> 并由 [Jordi Noguera](https://www.linkedin.com/in/jordinoguera/) 
> 使用 [Andrea Velázquez](https://www.linkedin.com/in/andreavelazquez1/) 的 UX 咨询构建。



## 介绍

如果你已经研究过云原生应用和技术，那么你可能已经偶遇过 [CNCF 云原生景观图](https://landscape.cncf.io)相关内容。这并不奇怪，其规模之大可能会让你不知所措。其中有那么多类别和那么多技术，你要如何理清它们呢？

和其他任何技术一样，如果把它分解开来并逐个分析，你会发现它并不那么复杂，而且非常合情合理。事实上，这张地图是按功能整齐地组织起来的，当你理解了每个类别所代表的含义，就很容易用它来”导航”了。

在本指南中，我们会逐步拆解这个巨大的景观，并提供其层次、列和类别的高层次概述。

### 什么是云原生景观图？

云原生景观图的目标是将所有云原生开源项目和专有产品分类编写并组织起来，提供当前云原生生态系统的概览。拥有云原生项目或产品的组织可以[提交PR](https://github.com/cncf/landscape/)来请求将其添加到景观图中。

### 如何使用本指南

在本指南中，景观图中每一层和列都有一章讨论其中的每个类别。类别有：它是什么，它解决什么问题，它如何帮助（解决问题）以及 technical 101。前三个部分都假定读者是没有技术背景的情况， technical 101则面向刚开始使用云原生的工程师。我们还包括了一个相关术语和 CNCF 项目列表的部分。


![CNCF Landscape](https://landscape.cncf.io/images/landscape_preview.png "CNCF Landscape")

> ##### 信息框
>
> 观察这个景象，你会注意到一些区别：
>  * *大盒子中的项目* 是CNCF托管的开源项目。有些仍处于孵化阶段（浅蓝/紫色边框），而其他则是毕业项目（深蓝色边框）。
>  * *小白盒子中的项目* 是开源项目。
>  * *灰色盒子中的产品* 是专利产品。
>
> 请注意新项目正在不断成为CNCF的一部分，因此请多多参考实际的景观图 - 事物日新月异！

<section data-category="Provisioning">
## 供应层

供应层是云原生景观图中的第一层。它包括用于创建和加固云原生应用程序构建基础的工具。在这里你将找到自动配置、创建和管理基础设施的工具，以及用于扫描、签名和存储容器镜像的工具。该层还扩展到安全领域，具备使策略设置和执行、嵌入式身份验证和授权以及处理密钥分发的工具。这听起来很拗口，所以让我们一个一个类别来讨论。

</section>

<section data-subcategory="Automation & Configuration" 
         data-buzzwords="Infrastructure-as-Code (IaC), Automation, Declarative Configuration">

### 自动化与配置 (Automation and Configuration)

#### 它是什么

自动化和配置工具可以加快计算资源（虚拟机、网络、防火墙规则、负载均衡器等）的创建和配置速度。此类工具可以处理供应过程的不同部分，或者尝试控制整个过程。大多数提供与该领域中其他项目和产品集成的能力。

#### 它解决什么问题

传统上，IT流程依赖于漫长而费力的手动发布周期，通常在三到六个月之间。这些周期伴随着许多人类过程和控制，使得生产环境的变化变得缓慢。这些缓慢的发布周期和静态环境与云原生开发不兼容。为了实现快速的开发周期，基础架构必须动态且没有人为干预地进行配置。

#### 它如何帮助（解决问题）

这类工具允许工程师在没有人为干预的情况下构建计算环境。通过对环境设置进行编码，它变得可重现，只需点击一个按钮。虽然手动设置容易出错，但一旦编码，环境创建就可以匹配精确的期望状态-这是一个巨大的优势。

虽然工具可能采取不同的方法，但它们都旨在通过自动化减少所需的资源配置工作。

#### Technical 101

随着我们从旧的人力驱动的配置向由云驱动的新的按需扩展模型迁移，我们之前使用的模式和工具已不再满足我们的需求。大多数组织无法承担一个大型的 7x24 员工团队来创建、配置和管理服务器。像 Terraform 这样的自动化工具可以减少扩展数十个服务器和拥有数百个防火墙规则的网络所需的工作量。像 Puppet、Chef 和 Ansible 这样的工具可以按编程方式配置这些新服务器和应用程序，在它们启动时允许开发人员使用它们。

一些工具直接与 AWS 或 vSphere 等平台提供的基础设施 API 进行交互，而其他工具则专注于配置单个机器，使它们成为 Kubernetes 集群的一部分。许多工具，如 Chef 和 Terraform，可以互操作以配置和管理环境。还有其他工具，如 OpenStack，旨在于提供其他工具可以使用的基础设施即服务（Infrastructure-as-a-Service IaaS）环境。从根本上说，在铺设计算环境、CPU、内存、存储和网络的基础上，您将需要一个或多个工具来创建和管理Kubernetes集群。您还需要这些工具的子集来创建和管理Kubernetes集群本身。

现在，这个领域已经有5个CNCF项目，如果算上Cluster API这样的项目，这还会更多。还有其他开源和供应商提供的非常强大的工具。

</section>

<section data-subcategory="Container Registry" 
         data-buzzwords="Container, OCI Image, Registry">

### 容器注册表


#### 它是什么

在深入了解容器注册表之前，我们需要定义三个紧密相关的概念：

* **容器**是“由计算机操作系统管理的具有资源和能力约束的运行进程”（参见 [云原生词汇表](https://github.com/cncf/glossary/blob/main/content/en/container.md)）。
* **镜像**是一组归档文件，用于运行容器及其进程。您可以将其视为模板，可在其上创建无限数量的容器。
* **仓库**或称为 repo ，是存储镜像的空间。

而**容器注册表**是专门的 Web 应用程序，可分类和存储仓库。

让我们快速回顾一下：镜像包含执行程序所需的信息（在容器中），并存储在仓库中，这些仓库又分为类别和组别，并存储在注册表中。构建、运行和管理容器的工具需要访问这些镜像。访问是通过引用注册表（访问镜像的路径）提供的。

#### 它解决什么问题
云原生应用程序被打包并作为容器运行。容器注册表存储并提供运行这些应用程序所需的容器镜像

#### 它如何帮助（解决问题）
通过集中存储所有容器镜像到一个地方，任何开发此应用程序的开发人员都可以轻松访问。

#### Technical 101
容器注册表存储和分发镜像或以某种方式增强现有注册表。根本上讲，注册表是允许容器运行时存储和检索镜像的 Web API。许多提供接口，允许容器扫描或签名工具增强其存储的镜像的安全性。有些专门于以特别高效的方式分发或复制镜像。任何使用容器的环境都需要使用一个或多个注册表。

这个领域的工具提供了集成，可以扫描、签名和检查它们存储的镜像。Dragonfly 和 Harbor 是 CNCF 项目，Harbor 最近获得了[第一个](https://goharbor.io/blog/harbor-2.0/)支持 OCI 的注册表的荣誉。每个主要的云提供商都提供自己的托管注册表，许多其他注册表可以独立部署，或通过像 Helm 这样的工具直接部署到您的 Kubernetes 集群中。

</section>

<section data-subcategory="Security & Compliance" 
         data-buzzwords="Image scanning, Image signing, Policy enforcement, Audit, Certificate Management">

### 安全和合规性

#### 它是什么

云原生应用程序旨在快速迭代。想想你手机上持续不断的应用更新——它们每天都在发展，假定变得更好了。为了按照一定节奏发布代码，您必须确保代码和操作环境是安全的，并且只能由授权工程师访问。本节中的工具和项目提供了构建和运行现代应用程序所需的一些能力。

#### 它解决什么问题

安全和合规性工具可帮助加固、监控和执行平台和应用程序的安全性。从容器到 Kubernetes 环境，这些工具允许您设置策略（用于合规性）、获取现有漏洞的洞察力、捕获错误配置并加固容器和集群。

#### 它如何帮助（解决问题）

要安全地运行容器，必须扫描容器中已知的漏洞并签名以确保它们没有被篡改。默认情况下，Kubernetes 具有极其宽松的访问控制设置，不适合生产使用。结果：Kubernetes 集群成为任何试图攻击您系统的人的一个有吸引力的目标。这个领域的工具和项目有助于加固集群并检测系统异常行为。

#### Technical 101

* 审计和合规性
* 生产路径：
  * 代码扫描
  * 漏洞扫描
  * 映像签名
* 策略创建和执行
* 网络层安全
其中一些工具很少直接使用。例如，Trivy、Claire 和 Notary 是由注册表或其他扫描工具利用的。其他则代表现代应用平台的关键加固组件。例如 Falco 或 Open Policy Agent (OPA)。

您会发现许多成熟的供应商提供此领域的解决方案以及专门创立的初创企业，旨在将 Kubernetes 原生框架引入市场。在撰写本文时，Falco、Notary/TUF 和 OPA 是 CNCF 项目中的一部分。

</section>

<section data-subcategory="Key Management" 
         data-buzzwords="AuthN and AuthZ, Identity, Access, Secrets">

### 密钥管理

#### 它是什么

在深入研究密钥管理之前，让我们先定义加密密钥。密钥是用于加密或签名数据的字符字符串。像物理钥匙一样，它给数据上锁（加密），以便只有具有正确密钥的人可以解锁（解密）。

随着应用程序和操作适应新的云原生世界，安全工具正在发展以满足新的安全需求。这个类别中的工具和项目涵盖了从如何安全地存储密码和其他秘密（敏感数据，如API密钥，加密密钥等）到如何安全地从您的微服务环境中消除密码和秘密的所有事情。

#### 它解决什么问题

云原生环境高度动态，需要按需进行秘密分发。这意味着必须做到完全编程化（没有人在环节中）和完全自动化。

此外，应用程序需要知道给定请求是否来自有效来源（身份验证），以及该请求是否有权执行其正在尝试执行的操作（授权）。 这通常称为 AuthN 和 AuthZ 。

#### 它如何帮助（解决问题）

每个工具或项目采取不同的方法，但它们都提供一种方法，无论是安全分发秘密和密钥，还是与身份验证，授权或两者都有关的服务或规范。

#### Technical 101

该类别的工具可分为两类：（1）密钥生成、存储、管理和轮换，以及 （2）单点登录和身份管理。例如，Vault 是一个相当通用的密钥管理工具，可让您管理不同类型的密钥。另一类的例子，Keycloak 是一个身份代理，可用于管理不同服务的访问密钥。

</section>

### 总结：供应层

正如我们所看到的，供应层的重点是使用工具构建云原生平台和应用程序的基础，这些工具处理从基础设施供应到容器注册表再到安全性的所有内容。接下来，我们将讨论包含云本地存储、容器运行时和网络的运行时层。

<section data-category="Runtime">

## 运行时

现在我们已经建立了云原生环境的基础，我们将向上移动一层基础设施，并放大到运行时层。它包含容器在云原生环境中运行所需的一切。这包括用于启动容器的代码，称为容器运行时；使持久存储可用于容器的工具；以及管理容器环境网络的工具。

但请注意，这些资源不应与上面讨论的供应层处理的网络和存储工作混淆。那些专注于使容器平台运行。这个类别中的工具用于启动和停止容器，帮助它们存储数据，并允许它们彼此交流。

</section>

<section data-subcategory="Cloud Native Storage"
         data-buzzwords="Persistent volume, CSI, Storage API, Backup and restore">

### 云原生储存 

#### 它是什么

存储是应用程序持久数据存储的地方，通常称为持久卷。为了可靠运行，应用程序需要轻松访问存储。通常来说，当我们说持久数据时，我们指的是存储数据库、消息或任何其他要确保在应用程序重新启动时不会消失的信息。

#### 它解决什么问题

云原生架构非常流动、灵活和弹性，这使得在重启之间持久化数据变得非常具有挑战性。为了进行扩展和自我修复，容器化应用程序不断地被创建和删除，随着时间推移而改变其物理位置。这就是为什么云原生存储必须提供独立于节点的功能。然而，要存储数据，您需要硬件，具体来说是一个磁盘，而磁盘就像任何其他硬件一样，都与基础设施绑定，这是我们面临的第一个重大挑战。

然后，实际的存储接口在数据中心之间可能会有很大的变化（在旧世界中，每个基础设施都有自己的存储解决方案和独特的接口），这使得可移植性非常困难。

最后，手动配置和自动扩展不兼容，因此，为了从云的弹性中受益，必须自动配置存储。

云原生存储是为这种新的云原生现实量身定制的。

#### 它如何帮助（解决问题）

这个类别中的工具可以帮助：

1. 为容器提供云原生存储选项，
2. 标准化容器和存储提供商之间的接口，或者
3. 通过备份和恢复操作提供数据保护。

前者意味着使用与云原生兼容的容器存储接口的存储（第二类工具），可以自动配置，通过消除人类瓶颈实现自动扩展和自我修复。

#### Technical 101

云原生存储主要得益于容器存储接口 (CSI)，该接口为容器提供提供文件和块存储的标准 API。在这一类别中有许多工具，包括开源和供应商提供的工具，它们利用 CSI 为容器提供按需存储。

此外，还有一些技术旨在解决其他云原生存储难题。Minio 是一个流行的项目，它提供了 S3 兼容的对象存储 API 等功能。像 Velero 这样的工具有助于简化备份和恢复 Kubernetes 集群本身以及应用程序使用的持久数据的过程。

</section>

<section data-subcategory="Container Runtime"
         data-buzzwords="Container, MicroVM">

### 容器运行时

#### 它是什么

如在容器注册表下所讨论的，容器是一组用于执行（或启动）应用程序的计算约束。容器化的应用程序认为它们正在运行在自己专用的计算机上，并且不知道它们正在与其他进程共享资源（类似于虚拟机）。

容器运行时是执行容器化（或“约束”）应用程序的软件。如果没有运行时，您只有容器映像，即静态文件，指定容器化的应用程序应该如何运行。运行时将在容器中启动应用程序并为其提供所需的资源。

#### 它解决什么问题

容器映像（应用程序规范的文件）必须以标准化、安全和隔离的方式启动。标准化是因为无论在哪里运行，都需要标准化的操作规则。安全，因为您不希望任何未经授权的人访问它。而隔离是因为您不希望应用程序受到其他应用程序的影响（例如如果共存的应用程序崩溃了）。隔离基本上起到保护作用。此外，还需要为应用程序提供资源，例如 CPU、存储和内存。

#### 它如何帮助（解决问题）

容器运行时完成所有这些工作。它以标准化的方式在所有环境中启动应用程序，并设置安全边界。后者是一些工具的区别所在。像 CRI-O 或 gVisor 这样的运行时已经加强了其安全边界。运行时还为容器设置资源限制。如果没有它，应用程序可能会根据需要消耗资源，潜在地占用其他应用程序的资源，因此您始终需要设置限制。

#### Technical 101

这个类别中不是所有的工具都是平等的。Containerd（著名的 Docker 产品的一部分）和 CRI-O 是标准容器运行时实现。然后有一些工具将容器的使用扩展到其他技术，例如 Kata，它允许您将容器作为VM运行。其他项目旨在解决特定的容器相关问题，例如 gVisor 在容器和操作系统之间提供了一个额外的安全层。

</section>

<section data-subcategory="Cloud Native Network"
         data-buzzwords="SDN, Network Overlay, CNI">

### 云原生网络

#### 它是什么

Containers talk to each other and to the infrastructure layer through a cloud native network. 
[Distributed applications](https://thenewstack.io/primer-distributed-systems-and-cloud-native-computing/) 
have multiple components that use the network for different purposes. Tools in this category create 
a virtual network on top of existing networks specifically for apps to communicate, referred to 
as an **overlay network**.

容器通过云原生网络相互通信和与基础架构层通信。 [分布式应用程序](https://thenewstack.io/primer-distributed-systems-and-cloud-native-computing/)  包含多个使用网络进行不同用途的组件。此类工具在现有网络的基础上创建一个虚拟网络，专门用于应用程序通信，称为**覆盖网络**。

#### 它解决什么问题

虽然人们通常称在容器中运行的代码为应用程序，但事实上，大多数容器仅包含大型应用程序的一小部分特定功能。像 Netflix 或 Gmail 这样的现代应用程序由许多这些较小的组件组成，每个组件都在自己的容器中运行。为了使所有这些独立的部分作为一个协调的应用程序运行，容器需要私下相互通信。这类工具提供了私有通信网络。

在容器之间流动的数据和消息可能具有敏感或私密数据。由于云原生网络使用软件来控制、检查和修改数据流，从而让管理、安全和隔离容器之间的连接更容易。在某些情况下，您可能希望扩展容器网络和网络策略，如防火墙和访问规则，以允许应用程序连接到容器网络之外运行的虚拟机或服务。云原生网络的可编程性和通常声明性使这种扩展成为可能。

#### 它如何帮助（解决问题）

该类别中的项目和产品使用容器网络接口（CNI），这是CNCF项目，为容器化应用程序提供网络功能。一些工具，如Flannel，相当简约，仅提供与容器的基本连接。其他工具，如 NSX-T，提供完整的软件定义网络层，为每个Kubernetes名称空间创建一个隔离的虚拟网络。

至少，容器网络需要为Pod（即在Kubernetes中运行容器化应用程序的地方）分配IP地址，以允许其他进程访问它。

#### Technical 101

这个领域的多样性和创新主要是由CNI（类似于上面提到的存储和容器存储接口）实现的。CNI 规范了网络层向pod提供功能的方式。选择适合你的 Kubernetes 环境的容器网络非常关键，你有许多工具可以选择。Weave Net、Antrea、Calico和 Flannel 都提供了有效的开源网络层。它们的功能差异很大，你的选择应该最终由你的特定需求驱动。

许多供应商使用软件定义网络（SDN）工具支持和扩展 Kubernetes 网络，提供对网络流量的额外见解，执行网络策略，甚至将容器网络和策略延伸到你的更广泛的数据中心。

</section>

### 总结：运行时

这是我们对运行时层的概述，它为容器提供了在云原生环境中运行所需的所有工具：

* 云原生存储为应用程序提供了易于快速访问所需数据以实现可靠运行的能力
* 容器运行时创建并启动容器，执行应用程序代码
* 云原生网络为容器化应用程序提供了通信的连接。

<section data-category="Orchestration & Management">

## 编排和管理

现在，我们已经覆盖了供应和运行时层，可以深入研究编排和管理层。在这里，您将找到处理运行和连接云原生应用程序的工具。此部分涵盖了从 Kubernetes 本身到负责应用程序内部和外部通信的基础设施层的所有内容。云原生应用程序具有固有的可扩展性，依赖于这些工具提供的自动化和弹性。

</section>

<section data-subcategory="Scheduling & Orchestration"
         data-buzzwords="Cluster, Scheduler, Orchestration">

### 编排和调度

#### 它是什么

编排和调度是指在集群中运行和管理[容器](https://github.com/cncf/glossary/blob/main/content/en/container.md)。集群是一组机器，可以是物理的或虚拟的，通过网络相连（参见云原生网络）。

容器编排器（和调度器）有些类似于您笔记本电脑上的操作系统（OS）。操作系统管理您所有的应用程序，如 Microsoft 365、Slack 和 Zoom；执行它们，并安排每个应用程序何时使用您笔记本电脑的硬件资源，如CPU、内存和存储器。

虽然在单个计算机上运行所有内容非常好，但今天的大多数应用程序都比一个计算机能够处理的要大得多。想想 Gmail 或者是 Netflix。这些巨大的应用程序分布在多台机器上，形成[分布式应用](https://thenewstack.io/primer-distributed-systems-and-cloud-native-computing/)。大多数现代应用程序都是这样构建的，需要能够管理在这些不同机器上运行的所有组件的软件。简而言之，您需要一个“集群操作系统”。这就是编排工具发挥作用的地方。

您可能已经注意到容器一次又一次地出现。它们在许多不同的环境中运行应用程序的能力是关键。在大多数情况下，容器编排器（Kubernetes）提供管理这些容器的能力。容器和 [Kubernetes](https://kubernetes.io/) 都是云原生架构的核心，这就是为什么我们经常听到它们的原因。

#### 它解决什么问题

如在“云原生网络”部分所述，在云原生体系结构中，应用程序被分解为小组件或服务，每个服务放置在容器中。你可能听说过它们被称为[微服务](https://github.com/cncf/glossary/blob/main/content/en/microservices-architecture.md)。现在，你不再有一个大型应用程序（通常被称为“巨石系统”），而是有几十甚至数百个（微）服务。每个服务都需要资源、监控和修复，如果出现问题。虽然针对单个服务手动完成所有这些工作可能是可行的，但在处理具有自己容器的多个服务时，你需要自动化的流程。

#### 它如何帮助（解决问题）

容器编排工具自动化了容器管理。但这在实践中意味着什么？让我们来回答一下 Kubernetes 的情况，因为它是事实上的容器编排工具。

Kubernetes 做的事情被称为期望状态协调：它将集群中容器的当前状态与期望状态匹配。期望状态由工程师指定（例如，在三个节点（即机器）上运行十个服务 A 实例，并访问数据库 B 等），并不断与实际状态进行比较。如果期望和实际状态不匹配，Kubernetes 通过创建或销毁对象来协调它们。例如，如果一个容器崩溃了，Kubernetes 就会启动一个新的容器。

简而言之，Kubernetes 允许您将集群视为一个计算机。它只关注环境应该看起来像什么，并为您处理实现细节。

#### Technical 101

Kubernetes 位于编排和调度层，与 Docker Swarm 和 Mesos 等其他容器编排器一起，以声明性方式管理多个不同的计算机资源池。 Kubernetes 中的声明性配置管理是通过[控制循环](https://kubernetes.io/docs/concepts/architecture/controller/)处理的，这是一种模式，其中在 Kubernetes 中运行的进程监视特定对象类型的 Kubernetes 存储，并确保群集中的实际状态与期望状态相匹配。

例如，用户创建了一个 Kubernetes 部署，指定必须有3个Web应用程序副本。部署控制器将确保创建这3个 Web 应用程序容器，然后继续监视群集，以查看容器数量是否正确。如果由于任何原因删除了特定容器，部署控制器将导致创建新实例。如果将部署修改为缩小到1个Web应用程序实例，则会指示 Kubernetes 删除2个正在运行的 Web 应用程序。

此核心控制器模式也可用于由用户或软件开发人员扩展 Kubernetes 。操作员模式允许人们为自定义资源编写自定义控制器，并在Kubernetes本身中构建任意逻辑和自动化。

虽然 Kubernetes 不是 CNCF 托管的唯一编排器（Crossplane 和 Volcano 都是沙盒项目），但它是最常用和活跃维护的编排器。

</section>

<section data-subcategory="Coordination & Service Discovery"
         data-buzzwords="DNS, Service Discovery">

### 协调和服务发现

#### 它是什么

现代应用程序由多个单独的服务组成，这些服务需要协作才能为最终用户提供价值。为了协作，它们通过网络通信（参见云原生网络），为了通信，它们必须首先找到彼此。服务发现是找出如何做到这一点的过程。

#### 它解决什么问题

云原生架构是动态和流动的，这意味着它们不断变化。当容器在一个节点上崩溃时，会在另一个节点上旋转一个新的容器以替换它。或者，当应用程序扩展时，副本会分散在整个网络中。没有一个特定服务的位置 - 一切的位置都在不断改变。此类工具跟踪网络内的服务，以便服务在需要时可以找到彼此。

#### 它如何帮助（解决问题）

服务发现工具通过提供一个共同的位置来查找和识别个别服务来解决此问题。在此类别中基本上有两种工具:

1. **服务发现引擎**：类似数据库的工具，存储有关所有服务及其定位方法的信息
2. **名称解析工具**：接收服务定位请求并返回网络地址信息的工具（例如 CoreDNS）

> ##### INFOBOX

> 在 Kubernetes 中，为了使 pod 可达性，引入了一个新的抽象层，称为“服务”。服务为动态更改的一组 pod 提供了单一的稳定地址。

> 请注意，“服务”在不同的上下文中可能具有不同的含义，这可能非常令人困惑。术语“服务”通常指放置在容器和 pod 中的服务。它是应用程序组件或微服务，具有实际应用程序中特定功能，例如移动电话的面部识别算法。

> Kubernetes 服务是指帮助 pod 找到并相互连接的抽象。它是服务（功能）的入口点，作为一组进程或 pod。在 Kubernetes 中，当您创建服务（抽象）时，您创建一组 pod，这些 pod 共同提供具有单一端点（入口点）的服务（一个或多个容器中的功能），该端点是 Kubernetes 服务。

#### Technical 101

随着分布式系统越来越普及，传统的 DNS 过程和传统的负载均衡器经常无法跟上不断变化的端点信息。为了弥补这些不足，服务发现工具处理单个应用程序实例快速注册和注销自己。一些选项，如 CoreDNS 和 etcd 是 CNCF 项目，并内置于 Kubernetes 中。其他工具则有自定义库或工具，可以使服务有效运作。

</section>

<section data-subcategory="Remote Procedure Call"
         data-buzzwords="gRPC">

### 远程过程调用

#### 它是什么

远程过程调用（RPC）是一种特定的技术，使应用程序能够相互通信。这是一种应用程序通信结构的方式。

#### 它解决什么问题

现代应用程序由许多单独的服务组成，这些服务必须进行通信才能协作。RPC是处理应用程序之间通信的一种选择。

#### 它如何帮助（解决问题）

RPC 提供一种紧密耦合和高度可选择的处理服务之间通信的方式。它允许带宽高效的通信，并且许多编程语言支持 RPC 接口实现。

#### Technical 101

使用 RPC 有很多潜在的好处：它使编码连接更容易，允许在网络层上实现极其高效的使用和服务之间的良好结构化通信。但是，RPC 也因为创建脆弱的连接点和迫使用户对多个服务进行协调升级而受到批评。gRPC 是一种特别流行的 RPC 实现，已被 CNCF 采用。

</section>

<section data-subcategory="Service Proxy"
         data-buzzwords="Service Proxy, Ingress">

### 服务代理

#### 它是什么

服务代理是一种工具，它拦截到或从给定服务出发的流量，应用一些逻辑，然后将该流量转发到另一个服务。它本质上充当一个“中间人”，可以收集有关网络流量的信息以及对其应用规则。这可以是简单的负载均衡器，将流量转发到单个应用程序，也可以是互联的代理网格，与单个容器化应用程序并行运行，处理所有网络连接。

服务代理本身就很有用，而在在将流量从更广泛的网络驱动特别是到 Kubernetes 集群时，服务代理也是其他系统的构建块。例如 API 网关或服务网格，我们将在下面讨论。

#### 它解决什么问题

应用程序应以受控方式发送和接收网络流量。为了跟踪流量并可能转换或重定向它，我们需要收集数据。传统上，启用数据收集和网络流量管理的代码嵌入在每个应用程序中。

服务代理“外部化”了此功能。它不再必须存在于应用程序中。相反，它嵌入在平台层（您的应用程序运行的位置）。这非常强大，因为它允许开发人员完全专注于编写生成价值的应用程序代码，从而允许处理流量的通用任务由平台团队管理，这首先应该是他们的责任。从单个公共位置集中分发和管理全球所需的服务功能（例如路由或 TLS 终止）可使服务之间的通信变得更加可靠，安全和高效。

#### 它如何帮助（解决问题）

代理作为用户与服务或不同服务之间的门卫。由于其独特的位置，它们提供了对正在发生的通信类型的洞察，并可以确定将特定请求发送到何处，甚至完全拒绝它。

代理收集关键数据，管理路由（在服务之间平均分配流量或在某些服务发生故障时重新路由），加密连接并缓存内容（减少资源消耗）。

#### Technical 101

服务代理通过拦截服务之间的流量，对其进行逻辑处理，并允许其在允许的情况下继续移动。嵌入到代理中的集中控制功能使管理员能够完成几件事情。他们可以收集有关服务间通信的详细指标，保护服务免受过载，并对服务应用其他常见标准，例如相互 TLS。对于像服务网格这样的工具，服务代理是基础的，因为它们提供了一种将更高级别的策略强制应用于所有网络流量的方式。

请注意，CNCF 将负载均衡器和入口提供程序包括在此类别中。

</section>

<section data-subcategory="API Gateway"
         data-buzzwords="API Gateway">

### API 网关

#### 它是什么

人类通常通过 GUI（图形用户界面）与计算机程序交互，例如网页或桌面应用程序，而计算机通过 API（应用程序编程接口）相互交互。但 API 不应与 API 网关混淆。

API 网关允许组织将关键功能（如授权或限制应用程序之间的请求数量）移动到集中管理的位置。它还作为（通常是外部的）API 消费者的公共接口。

#### 它解决什么问题

虽然大多数容器和核心应用程序都有一个 API，但 API 网关不仅仅是一个 API。API 网关简化了组织如何管理和应用规则到所有交互。

API 网关允许开发人员编写和维护更少的自定义代码（系统功能被编码在 API 网关中，还记得吗？）。它们还使团队能够查看和控制应用程序用户与应用程序本身之间的交互。

#### 它如何帮助（解决问题）

API网关位于用户和应用程序之间。它充当一个中间代理，接收用户的消息（请求），并将其转发到适当的服务。但在移交请求之前，它会评估用户是否被允许做他们想做的事情，并记录有关谁发出请求以及他们发出了多少请求的详细信息。

简而言之，API网关为应用程序用户提供一个单一的入口点，具有常见的用户界面。它还使您能够将在应用程序中实现的任务移交给网关，从而节省开发人员的时间和金钱。

> ##### 示例
> 以亚马逊商店卡为例。为了提供它们，亚马逊与一家银行合作，该银行将发行和管理所有亚马逊商店卡。作为回报，银行将保留每笔交易的1美元。银行将使用API网关来授权零售商请求新卡，跟踪结算的交易数量，甚至可能限制每分钟请求的卡数。所有这些功能都编码到网关中，而不是使用它的服务。服务只关心发卡。

#### Technical 101

像代理和服务网格（见下文）一样，API 网关将自定义代码从我们的应用程序中取出并引入到中央系统中。API 网关通过拦截对后端服务的调用来工作，执行某种增值活动，例如验证授权、收集度量或转换请求，然后执行它认为合适的任何操作。

API 网关为一组下游应用程序提供一个共同的入口点，同时提供一个团队可以注入业务逻辑来处理授权、速率限制和计费的地方。它们允许应用程序开发人员将对其下游 API 的更改抽象出来，使其客户无需关注，同时将像新客户入门这样的任务卸载到网关。

</section>

<section data-subcategory="Service Mesh"
         data-buzzwords="Service mesh, Sidecar, Data plane, Control plane">

### 服务网格

#### 它是什么

服务网格管理服务之间的流量（即通信）。它们使平台团队能够在集群内运行的所有服务中统一添加可靠性、可观察性和安全功能，而无需进行任何代码更改。

与 Kubernetes 一起，服务网格已成为云原生堆栈中最重要的基础架构组件之一。

#### 它解决什么问题

在云原生世界中，我们处理多个服务需要通信。这意味着更多的流量在本质上不可靠且常常缓慢的网络上来回传递。为了解决这个新的一系列挑战，工程师必须实现额外的功能。在服务网格之前，这些功能必须编码到每个应用程序中。这种定制代码经常成为技术债务的源头，并提供了新的失败或漏洞的途径。

#### 它如何帮助（解决问题）

服务网格在不触及应用程序代码的情况下，在平台层统一为所有服务添加可靠性、可观察性和安全性功能。它们兼容任何编程语言，使开发团队可以专注于编写业务逻辑。

> ##### 信息盒子
> 传统上，这些服务网格功能必须编码到每个服务中，每次发布或更新新服务时，开发人员必须确保这些功能也是可用的，从而提供了很大的人为错误空间。一个不为人知的秘密是，开发人员更喜欢专注于业务逻辑（产生价值的功能），而不是构建可靠性、可观察性和安全性功能。
> 对于平台所有者来说，这些是核心能力，是他们所做的一切的核心。让开发人员负责添加平台所有者需要的功能本质上是有问题的。顺便说一下，这也适用于上面提到的通用代理和API网关。服务网格和API网关解决了这个问题，因为它们由平台所有者实施，并普遍应用于所有服务。


#### Technical 101

服务网格通过服务代理将群集中运行的所有服务绑定在一起，从而创建服务网格。这些由服务网格控制平面进行管理和控制。服务网格允许平台所有者执行常见操作或收集有关应用程序的数据，而无需开发人员编写自定义逻辑。

实质上，服务网格是管理服务之间通信的基础结构层，通过向服务代理网络（您的网格）提供命令和控制信号来实现。它的强大之处在于它能够提供关键的系统功能，而无需修改应用程序。

一些服务网格使用通用的服务代理（如上所述）作为其数据平面。其他人使用专用代理；例如，Linkerd 使用 [Linkerd2-proxy “微代理”](https://linkerd.io/)来在性能和资源消耗方面获得优势。这些代理通过所谓的旁路附加到每个服务。边车（Sidedecar）是指代理在自己的容器中运行，但位于同一 pod 中。就像摩托车旁的边车一样，它是一个单独的模块，跟随摩托车走到哪里。

> ##### 例子
> 以熔断器为例。在微服务环境中，单个组件经常会失败或开始运行缓慢。如果没有服务网格，则开发人员将不得不编写自定义逻辑来优雅地处理下游故障，并可能设置冷却时间器，以避免上游服务不断请求来自降级或故障下游服务的响应。有了服务网格，该逻辑在平台级别处理。
> 服务网格提供许多有用的功能，包括显示详细的指标、加密所有流量、限制哪个服务被授权执行哪些操作、为其他工具提供附加插件等等。有关更详细的信息，请查看[服务网格接口](https://smi-spec.io/)规范。

</section>

### 总结：编排和管理

正如我们所看到的，这个层面的工具涉及如何作为一个组管理所有这些独立的容器化服务。编排和调度工具可以被视为一个集群操作系统，管理您集群中的容器化应用程序。协调和服务发现、服务代理以及服务网格确保服务可以相互找到并有效地通信，以协同作为一个一体化的应用。API 网关是提供更多控制服务间通信的额外层，特别是在外部应用程序之间。接下来，我们将讨论应用程序定义和开发层—— CNCF 景观的最后一层。它涵盖数据库、流媒体和消息传递、应用程序定义和镜像构建，以及持续集成和交付。

<section data-category="App Definition and Development">

## 应用程序定义和开发

到目前为止，我们讨论的所有内容都与构建可靠、安全的环境和提供所有必需的依赖项有关。现在，我们到达了CNCF云原生景观的顶层。顾名思义，应用程序定义和开发层专注于使工程师能够构建应用程序的工具。

</section>

<section data-subcategory="Database"
         data-buzzwords="SQL, DB, Persistence">

### 数据库

#### 它是什么

数据库是一种应用程序，通过该应用程序，其他应用程序可以高效地存储和检索数据。数据库允许您存储数据，确保只有经过授权的用户可以访问它，并通过专门的请求使用户可以检索它。虽然有许多不同类型的数据库具有不同的方法，但它们最终都具有相同的总体目标。

#### 它解决什么问题

大多数应用程序需要一种有效的方法来存储和检索数据，同时保持数据的安全性。数据库使用经过验证的技术以结构化方式完成此操作，尽管这需要相当复杂的技术。

#### 它如何帮助（解决问题）

数据库为应用程序提供了一个通用的接口来存储和检索数据。开发人员使用这些标准接口和相对简单的查询语言来存储、查询和检索信息。同时，数据库允许用户持续备份和保存数据，以及加密和管理对其的访问。

#### Technical 101

数据库是存储和检索数据的应用程序，使用一种通用的语言和接口，与许多不同的语言和框架兼容。

通常，有两种常见类型的数据库：结构化查询语言（SQL）数据库和 no-SQL 数据库（译者注：即关系型数据库和非关系型数据库，可以查阅 Design Data-intensive Application 这本书）。应该根据特定应用程序的需求和限制来确定它使用哪种数据库。

随着 Kubernetes 的兴起及其支持有状态应用程序的能力，我们看到了一批新一代数据库利用容器化的优势。这些新的云本地数据库旨在将 Kubernetes 的扩展性和可用性带到数据库中。像 YugabyteDB 和 Couchbase 这样的工具是云本地数据库的例子，尽管 MySQL 和 Postgres 等更传统的数据库也可以在 Kubernetes 集群中成功有效地运行。

Vitess 和 TiKV 是 CNCF 在这个领域的项目。

> ##### 信息框
> 
> 如果您查看此类别，您会注意到许多名称以 DB 结尾（例如MongoDB，CockroachDB，FaunaDB），您可能会猜到它代表数据库。您还会看到各种以 SQL 结尾的名称（例如 MySQL 或 memSQL）它们仍然相关。有些是“老派”的数据库已经适应了云本地的现实。还有一些数据库是非 SQL 但兼容 SQL 的，例如 YugabyteDB 和 Vitess。

</section>

<section data-subcategory="Streaming & Messaging"
         data-buzzwords="Choreography, Streaming, MQ, Message bus">

### 流和消息

#### 它是什么

为了实现共同的目标，服务需要相互通信并保持彼此联系。每当一个服务执行某个操作时，它会发送有关该特定事件的消息。

流和消息工具通过在系统之间传输消息（即事件）来实现服务与服务之间的通信。各个服务连接到消息服务以发布事件、从其他服务读取消息或两者兼而有之。这种动态创造了一种环境，其中各个应用程序要么是发布者，即它们编写事件，要么是订阅者，读取事件，或更可能是两者兼而有之。

#### 它解决什么问题

随着服务的增加，应用程序环境变得越来越复杂，使得应用程序之间的通信管理变得更具挑战性。流和消息平台提供了一个中心位置，用于发布和读取系统内发生的所有事件，使应用程序能够在不必了解彼此的情况下协同工作。

#### 它如何帮助（解决问题）

当服务执行其他服务应该知道的操作时，它会将事件“发布”到流式传输或消息传递工具。需要了解这些类型事件的服务会“订阅”并观察流式传输或消息传递工具。这就是发布-订阅或只是 pub-sub 方法的本质，由这些工具实现。

通过引入一个“中间”层来管理所有通信，我们将服务之间解耦。它们只需观察事件、执行操作并发布新事件。

举例来说。当你第一次注册 Netflix 时，“注册”服务会将“新注册事件”发布到消息平台，其中包括姓名、电子邮件地址、订阅级别等详细信息。订阅注册事件的“账户创建器”服务将看到该事件并创建你的账户。还订阅新注册事件的“客户通讯”服务将把你的电子邮件地址添加到客户邮件列表中并生成欢迎电子邮件等等。

这允许高度解耦的架构，在其中服务可以协作而无需知道彼此。这种解耦使工程师能够添加新功能而无需更新下游应用程序（即消费者）或发送一堆查询。系统解耦程度越高，越灵活、易于变更。这正是工程师在系统中所追求的。

#### Technical 101

在云原生成为主流之前，消息传递和流媒体工具一直存在。为了集中管理业务关键事件，组织机构建立了大型企业服务总线。但是，当我们谈论云原生上的消息传递和流媒体时，我们通常指的是像NATS、RabbitMQ、Kafka 或云提供的消息队列等工具。

这些系统的共同点在于它们所支持的架构模式。在云原生环境中，应用程序交互要么是被编排的，要么是被协调的。这方面还有很多内容，但我们可以简单地说，编排是指集中管理的系统，而协调是指允许各个组件独立地运行的系统。

消息传递和流媒体系统提供了一个中央位置，让协调的系统之间进行通信。消息总线提供了一个共同的位置，所有应用程序都可以通过发布消息来向其他应用程序告知自己正在做什么，或通过订阅消息来了解发生了什么。

NATS 和 Cloudevents 项目都是CNCF的孵化项目。NATS 提供了一个成熟的消息传递系统，而 Cloudevents 是一种标准化消息格式的努力，旨在实现不同系统之间的互通。Strimzi、Pravega 和Tremor是沙盒项目，每个项目都针对流媒体和消息传递的不同用例进行了优化。

</section>

<section data-subcategory="Application Definition & Image Build"
         data-buzzwords="Package Management, Charts, Operators">

### 应用程序定义和镜像构建

#### 它是什么

应用程序定义和镜像构建是一个广泛的类别，可分为两个主要子类。首先，面向开发人员的工具，可帮助将应用程序代码构建为容器和/或 Kubernetes。其次，面向运营的工具可以以标准化的方式部署应用程序。无论您是要加快还是简化开发环境，提供标准化的方式来部署第三方应用程序，还是希望简化编写新的 Kubernetes 扩展的过程，这个类别都有很多优化 Kubernetes 开发人员和运营商体验而设计的项目。

#### 它解决什么问题     

Kubernetes，或者更普遍的说容器化环境，具有极大的灵活性和强大的功能。随着这种灵活性的增加，也带来了复杂性，主要体现在多个配置选项以及各种用例的多种需求形式上。开发人员需要在将其代码容器化时创建可重复的图像。运营商需要以标准化的方式将应用程序部署到容器环境中，最后，平台团队需要提供工具，以简化内部和第三方应用程序的图像创建和应用程序部署过程。

#### 它如何帮助（解决问题）

Tools in this space aim to solve some of these developer or operator challenges. On the developer 
side, there are tools that simplify the process of extending Kubernetes to build, deploy, and 
connect applications. A number of projects and products help to store or deploy pre-packaged apps. 
These allow operators to quickly deploy a streaming service like NATS or Kafka or install a service 
mesh like Linkerd.

Developing cloud native applications brings a whole new set of challenges calling for a large set 
of diverse tools to simplify application build and deployments. As you start addressing operational 
and developer concerns in your environment, look for tools in this category.

#### Technical 101

Application definition and build tools encompass a huge range of functionality. From extending 
Kubernetes to virtual machines with KubeVirt, to speeding app development by allowing you to port 
your development environment into Kubernetes with tools like Telepresence. At a high level, tools 
in this space solve either developer-focused concerns, like how to correctly write, package, test, 
or run custom apps, or operations-focused concerns, such as deploying and managing applications.

Helm, the only graduated project in this category, underpins many app deployment patterns. Helm 
allows Kubernetes users to deploy and customize many popular third-party apps, and it has been 
adopted by other projects like the Artifact Hub (a CNCF sandbox project). Companies like Bitnami 
also provide curated catalogs of apps. Finally, Helm is flexible enough to allow users to customize 
their own app deployments and is often used by organizations for their own internal releases.

The Operator Framework is an incubating project aimed at simplifying the process of building and 
deploying operators. Operators are out of scope for this guide but let's note here that they help 
deploy and manage apps, similar to Helm (you can read more about operators 
[here](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)). Cloud Native Buildpacks, 
another incubating project, aims to simplify the process of building application code into 
containers.

There’s a lot more in this space and exploring it all would require a dedicated chapter. But 
research these tools further if you want to make Kubernetes easier for developers and operators. 
You’ll likely find something that meets your needs.

</section>

<section data-subcategory="Continuous Integration & Delivery"
         data-buzzwords="CI/CD, Continuous integration, Continuous delivery, Continuous deployment, Blue/green, Canary deploy">

#### 它是什么

Continuous integration (CI) and continuous delivery (CD) tools enable fast and efficient development 
with embedded quality assurance. CI automates code changes by immediately building and testing the 
code, ensuring it produces a deployable artifact. CD goes one step further and pushes the artifact 
through the deployment phases.

Mature CI/CD systems watch source code for changes, automatically build and test the code, then 
begin moving it from development to production where it has to pass a variety of tests or validation 
to determine if the process should continue or fail. Tools in this category enable such an approach.

#### 它解决什么问题

Building and deploying applications is a difficult and error-prone process, particularly when it 
involves a lot of human intervention and manual steps. The longer a developer works on a piece of 
software without integrating it into the codebase, the longer it will take to identify an error and 
the more difficult it will be to fix. By integrating code on a regular basis, errors are caught 
early and are easier to troubleshoot. After all, finding an error in a few lines of code is a lot 
easier than doing so in a few hundred lines of code, or, even worse, finding it once it reaches 
production.

While tools like Kubernetes offer great flexibility for running and managing apps, they also create 
new challenges and opportunities for CI/CD tooling. Cloud native CI/CD systems are able to 
leverage Kubernetes itself to build, run, and manage the CI/CD process, often referred to as a 
pipeline. Kubernetes also provides information about app health, enabling cloud native CI/CD tools 
to more easily determine if a given change was successful or should be rolled back.

#### 它如何帮助（解决问题）

CI tools ensure that any code change or updates developers introduce are built, validated, and 
integrated with other changes automatically and continuously. Each time a developer adds an update, 
automated testing is triggered to ensure only good code makes it into the system. CD extends CI to 
include pushing the result of the CI process into production-like and production environments.

Let's say a developer changes the code for a web app. The CI system sees the code change, then 
builds and tests a new version of that web app. The CD system takes that new version and deploys 
it into a dev, test, pre-production, and finally production environment. It does that while testing 
the deployed app after each step in the process. All together these systems represent a CI/CD 
pipeline for that web app.

#### Technical 101

Over time, a number of tools have been built to help with the process of moving code from a source 
code repository to production. Like most other areas of computing, the advent of cloud native 
development has changed CI/CD systems. Some traditional tools like Jenkins, probably the most 
prolific CI tool on the market, have [overhauled](https://jenkins-x.io/) themselves entirely to 
better fit into the Kubernetes ecosystem. Others, like Flux and Argo have pioneered a new way of 
doing continuous delivery called GitOps, which the OpenGitOps project is working to define as a
vendor-neutral standard.

In general, you’ll find projects and products in this space are either (1) CI systems, (2) CD 
systems, (3) tools that help the CD system decide if the code is ready to be pushed into production, 
or (4), in the case of Spinnaker and Argo, all three. Flux and Argo are CNCF gratuated projects in this 
space, Keptn is the CNCF incubating project, along with the CNCF sandbox projects 
OpenFeature, OpenGitOps and OpenKruise.
You can also find many more options hosted by the 
[Continuous Delivery Foundation](https://cd.foundation/). Look for tools in this space to help 
your organization automate your path to production.

</section>

### Summary: App Definition & Development

As we've seen, tools in the application definition and development layer enable engineers to build 
cloud native apps. You'll find databases to store and retrieve data or streaming and messaging 
tools allowing for decoupled, choreographed architectures. Application definition and image build 
tools include a variety of technologies that improve the developer and operator experience. 
Finally, CI/CD helps engineers catch any errors early on, ensuring code is ready for deployment 
by driving up  quality.

This chapter concludes the layers of the CNCF landscape. Next we'll focus on the observability and 
analysis "column."

<section data-category="Observability and Analysis">

Now that we've worked our way through the layers of the CNCF landscape, we'll focus on the columns 
starting with observability and analysis.

Before diving into these categories, let's first define observability and analysis. Observability 
is a system characteristic describing the degree to which a system can be understood from its 
external outputs. Measured by CPU time, memory, disk space, latency, errors, etc., computer systems 
can be more or less observable. Analysis is an activity in which you look at this observable data 
and make sense of it.

To ensure there is no service disruption, you'll need to observe and analyze every aspect of your 
application so every anomaly gets detected and rectified right away. This is what this category is 
all about. It runs across and observes all layers which is why it's on the side and not embedded 
in a specific layer.

Tools in this category are broken down into logging, monitoring, tracing, and chaos engineering. 
Please note that the category name is somewhat misleading — although chaos engineering is listed 
here, consider it a reliability tool rather than an observability or analysis tool.

</section>

<section data-subcategory="Monitoring"
         data-buzzwords="Monitoring, Time series, Alerting, Metrics">

#### 它是什么

Monitoring refers to instrumenting an app to collect, aggregate, and analyze logs and metrics to 
improve our understanding of its behavior. While logs describe specific events, metrics are a 
measurement of a system at a given point in time — they are two different things but both necessary 
to get the full picture of your system's health. Monitoring includes everything from watching disk 
space, CPU usage, and memory consumption on individual nodes to doing detailed synthetic 
transactions to see if a system or application is responding correctly and in a timely manner. 
There are a number of different approaches to monitor systems and applications.

#### 它解决什么问题

When running an application or platform, you want it to accomplish a specific task as designed and 
ensure it's only accessed by authorized users. Monitoring allows you to know if it is working 
correctly, securely, cost effectively, only accessed by authorized users, as well as any other 
characteristic you may be tracking.

#### 它如何帮助（解决问题）

Good monitoring allows operators to respond quickly, and even automatically, when an incident 
arises. It provides insights into the current health of a system and watches for changes. 
Monitoring tracks everything from application health to user behaviour and is an essential 
part of effectively running applications.

#### Technical 101

Monitoring in a cloud native context is generally similar to monitoring traditional applications. 
You need to track metrics, logs, and events to understand the health of your applications. The 
main difference is that some of the managed objects are ephemeral, meaning they may not be long 
lasting so tying your monitoring to objects like auto generated resource names won’t be a good long 
term strategy. There are a number of CNCF projects in this space that largely revolve around 
Prometheus, the CNCF graduated project.

</section>

<section data-subcategory="Logging"
         data-buzzwords="Logging">

#### 它是什么

Applications emit a steady stream of log messages describing what they are doing at any given time. 
These log messages capture various events happening in the system such as failed or successful 
actions, audit information, or health events. Logging tools collect, store, and analyze these 
messages to track error reports and related data. Along with metrics and tracing, logging is one 
of the pillars of observability.

#### 它解决什么问题

Collecting, storing, and analyzing logs is a crucial part of building a modern platform and 
logging performs one or all of those tasks. Some tools handle every aspect from collection to 
analysis while others focus on a single task like collection. All logging tools aim at helping 
organizations gain control over their log messages.

#### 它如何帮助（解决问题）

When collecting, storing, and analyzing application log messages, you'll understand what an 
application was communicating at any given time. But as logs only represent messages that 
applications or platforms deliberately emit, they don’t necessarily pinpoint the root cause of a 
given issue. That being said, collecting and retaining log messages over time is an extremely 
powerful capability and will help teams diagnose issues and meet regulatory and compliance 
requirements.

#### Technical 101

Collecting, storing, and processing log messages is by no means a new problem, but cloud native 
patterns and Kubernetes have significantly changed the way logs are handled. Some traditional 
approaches to logging that were appropriate for virtual and physical machines, like writing logs 
to a file on a local disk, are ill suited to containerized applications, where  file systems don't 
outlast an application. In a cloud native environment, log collection tools like Fluentd run 
alongside application containers and collect messages directly from the applications. Messages 
are then forwarded on to a central log store to be aggregated and analyzed.

Fluentd is the only CNCF project in this space.

</section>

<section data-subcategory="Tracing"
         data-buzzwords="Span, Tracing">

#### 它是什么

In a microservices world, services are constantly communicating with each other over the network. 
Tracing, a specialized use of logging, allows you to trace the path of a request as it moves 
through a distributed system.

#### 它解决什么问题

Understanding how a microservice application behaves at any given point in time is an extremely 
challenging task. While many tools provide deep insights into service behavior, it can be difficult 
to tie an action of an individual service to the broader understanding of how the entire app 
behaves.

#### 它如何帮助（解决问题）

Tracing solves this problem by adding a unique identifier to messages sent by the application. 
That unique identifier allows you to follow (or trace) individual transactions as they move through 
your system. You can use this information to see the health of your application as well as 
debug problematic microservices or activities.

#### Technical 101

Tracing is a very powerful debugging tool that allows you to troubleshoot and fine tune the 
behaviour of a distributed application. That power does come at a cost. Application code needs 
to be modified to emit tracing data and any spans (a representation of individual units of work 
done in a distributed system) need to be propagated by infrastructure components (e.g. service 
meshes and their proxies) in the data path of your application. Jaeger and Open Tracing are CNCF 
projects in this space.

</section>

<section data-subcategory="Chaos Engineering"
         data-buzzwords="Chaos Engineering">

#### 它是什么

Chaos engineering refers to the practice of intentionally introducing faults into a system in 
order to test its resilience and ensure applications and engineering teams are able to withstand 
turbulent and unexpected events. A chaos engineering tool will provide a controlled way to 
introduce faults and run specific experiments against a particular instance of an application.

#### 它解决什么问题  

Complex systems fail. They fail for a host of reasons and in a distributed system the consequences 
are typically hard to understand. Chaos engineering is embraced by organizations that accept that 
failures will occur and, instead of trying to prevent failures, practice recovering from them. 
This is referred to as optimizing for 
[mean time to repair](https://en.wikipedia.org/wiki/Mean_time_to_repair), or MTTR.

> ##### INFOBOX
> 
> The traditional approach to maintaining high availability for applications is referred to as 
> optimizing for [mean time between failures](https://en.wikipedia.org/wiki/Mean_time_between_failures), 
> or MTBF. You can observe this practice in organizations that use things like "change review 
> boards" and "long change freezes" to keep an application environment stable by restricting 
> changes. The authors of [Accelerate](https://itrevolution.com/accelerate-book/) suggest that 
> high performing IT organizations achieve high availability by optimizing for mean time to 
> recovery, or MTTR, instead.

#### 它如何帮助（解决问题）
In a cloud native world, applications must dynamically adjust to failures, a relatively new 
concept. That means, when something fails, the system doesn't go down completely but gracefully 
degrades or recovers. Chaos engineering tools enable you to experiment on a software system in 
production to ensure they perform gracefully should a real failure occur.

In short, you experiment with a system because you want to be confident that it can withstand 
turbulent and unexpected conditions. Instead of waiting for something to happen and find out, you 
place it under duress in controlled conditions to identify weaknesses and fix them before chance 
uncovers them for you.

#### Technical 101

Chaos engineering tools and practices are critical to achieving high availability for your 
applications. Distributed systems are often too complex to be fully understood by any one engineer 
and no change process can fully predetermine the impact of changes on an environment. By 
introducing deliberate chaos engineering practices teams are able to practice and automate 
failure recovery. Chaos Mesh and Litmus Chaos are two CNCF tools in this space.

</section>

### Summary: Observability & Analysis

As we've seen, the observability and analysis column is all about understanding the health of your 
system and ensuring it stays operational even under tough conditions. Logging tools capture event 
messages emitted by apps, monitoring watches logs and metrics, and tracing follows the path of 
individual requests. When combined, these tools ideally provide a 360 degree view of what's going 
on within your system. Chaos engineering is a little different. It provides a safe way to verify 
the system can withstand unexpected events, ensuring it stays healthy.

Next, we'll focus on cloud native platforms. Configuring tools across the landscape so they work 
well together is no easy task. Platforms bundle them together, easing adoption.

<section data-category="Platform">

As we've seen so far, each of the categories discussed solves a particular problem. Storage alone 
does not provide all you need to manage your app. You'll need an orchestration tool, a container 
runtime, service discovery, networking, an API gateway, etc. Platforms bundle different tools from 
different layers together, solving a larger problem.

There isn't anything inherently new in these platforms. Everything they do can be done by one of 
the tools in these layers or the observability and analysis column. You could certainly build your 
own platform and, in fact, many organizations do. However, configuring and fine-tuning the different 
modules reliably and securely while ensuring that all technologies are always kept up to date 
and vulnerabilities patched is no easy task—you'll need a dedicated team to build and maintain it. 
If you don't have the necessary resources or know-how, your team is likely better off with a 
platform. For some organizations, especially those with small engineering teams, platforms are the 
only way to adopt a cloud native approach.

You'll probably notice, all platforms revolve around 
[Kubernetes](https://github.com/cncf/glossary/blob/main/content/en/kubernetes.md). That's because 
is at the core of the cloud native stack.

</section>

<section data-subcategory="Certified Kubernetes - Distribution">

#### 它是什么

A distribution, or distro, is when a vendor takes core Kubernetes — that's the unmodified, open 
source code (although some modify it) — and packages it for redistribution. Usually this entails 
finding and validating the Kubernetes software and providing a mechanism to handle cluster 
installation and upgrades. Many Kubernetes distributions include other proprietary or open source 
applications.

#### What it addresses

[Open source Kubernetes](https://github.com/kubernetes/kubernetes) doesn’t specify a particular 
installation tool and leaves many setup configuration choices to the user. Additionally, there is 
limited support for issues as they arise through community resources like 
[Community Forums](https://discuss.kubernetes.io/), 
[StackOverflow](https://stackoverflow.com/questions/tagged/kubernetes), or 
[Slack](https://slack.k8s.io/).

While using Kubernetes has become easier over time, it can be challenging to find and use the open 
source installers. Users need to understand what versions to use, where to get them, and if a 
particular component is compatible with another. They also need to decide what software will be 
deployed to their clusters and what settings to use to ensure their platforms are secure, stable, 
and efficient. All this requires deep Kubernetes expertise that may not be readily available 
in-house.

#### 它如何帮助（解决问题）

Kubernetes distributions provide a trusted and reliable way to install Kubernetes and provide 
opinionated defaults that create a better and more secure operating environment. A Kubernetes 
distribution gives vendors and projects the control and predictability they need to provide support 
for a customer as they go through the lifecycle of deploying, maintaining, and upgrading their 
Kubernetes clusters.

That predictability enables distribution providers to support users when they have production 
issues. Distributions also often provide a tested and supported upgrade path that allows users 
to keep their Kubernetes clusters up to date. Additionally, distributions often provide software 
to deploy on top of Kubernetes that makes it easier to use.

Distributions significantly ease and speed up Kubernetes adoption. Since the expertise needed to 
configure and fine-tune the clusters is coded into the platform, organizations can get up and 
running with cloud native tools without having to hire additional engineers with specialized 
expertise.

#### Technical 101

If you've installed Kubernetes, you’ve likely used something like kubeadm to get your cluster up 
and running. Even then, you probably had to decide on a CNI, install, and configure it. Then, you 
might have added some storage classes, a tool to handle log messages, maybe an ingress controller, 
and the list goes on. A Kubernetes distribution will automate some or all of that setup. It will 
also ship with configuration settings based on its own interpretation of best practice or an 
intelligent default. Additionally, most distributions will come with some extensions or add-ons 
bundled and tested to ensure you can get going with your new cluster as quickly as possible.

There are a lot of options in this category. [k3s](https://k3s.io/) is the only CNCF project in 
this category. There are a lot of great open source and commercial options available. We encourage 
you to think carefully about your needs when you begin evaluating distributions.

</section>

<section data-subcategory="Certified Kubernetes - Hosted"
         data-buzzwords="Hosted">

#### 它是什么

Hosted Kubernetes is a service offered by infrastructure providers like AWS, Digital Ocean, Azure, 
and Google, allowing customers to spin up a Kubernetes cluster on-demand. The cloud provider 
takes responsibility for managing part of the Kubernetes cluster, usually called the control plane. 
They are similar to distributions but managed by the cloud provider on their infrastructure.

#### 它解决什么问题

Hosted Kubernetes allows teams to get started with Kubernetes without knowing or doing anything 
beyond setting up an account with a cloud vendor. It solves four of the five Ws of getting started 
with Kubernetes. Who (manages it): your cloud provider; what: their hosted Kubernetes offering; 
when: now; and where: on the cloud providers infrastructure. The why is up to you.

#### 它如何帮助（解决问题）

Since the provider takes care of all management details, hosted Kubernetes is the easiest way to 
get started with cloud native. All users have to do is develop their apps and deploy them on the 
hosted Kubernetes services — it's incredibly convenient. Hosted Kubernetes allows users to spin up 
a cluster and get started right away (with the exception of AWS' EKS which also requires users to 
take some additional steps to prepare their clusters) while taking some responsibility for the 
cluster availability. It’s worth noting that with the extra convenience of these services comes 
some reduced flexibility. The offering is bound to the cloud provider, and Kubernetes users don’t 
have access to the control plane.

#### Technical 101

Hosted Kubernetes are on-demand Kubernetes clusters provided by a vendor, usually an infrastructure 
hosting provider. The vendor takes responsibility for provisioning the cluster and managing the 
Kubernetes control plane. Again, the notable exception is EKS, where individual node provisioning 
is left up to the client.

Hosted Kubernetes allows an organization to quickly provision new clusters and reduce their 
operational risk by outsourcing infrastructure component management to another organization. The 
main trade-offs are that you’ll likely be charged for the control plane management and that you'll 
be limited in what you can do. Managed clusters provide stricter limits on configuring your 
Kubernetes cluster than DIY Kubernetes clusters.

</section>

<section data-subcategory="Certified Kubernetes - Installer"
         data-buzzwords="Installer">

#### 它是什么

Kubernetes installers help install Kubernetes on a machine. They automate the Kubernetes 
installation and configuration process and may even help with upgrades. Kubernetes installers 
are often coupled with or used by Kubernetes distributions or hosted Kubernetes offerings.

#### 它解决什么问题  

Similar to Kubernetes distributions, Kubernetes installers simplify getting started with 
Kubernetes. Open source Kubernetes relies on installers like kubeadm which, as of this writing, 
is part of the Certified Kubernetes Administrator certification exam to get Kubernetes clusters 
up and running.

#### 它如何帮助（解决问题）

Kubernetes installers ease the Kubernetes installation process. Like distributions, they provide a 
vetted source for the source code and version. They also often ship with opinionated Kubernetes 
environment configurations. Kubernetes installers like [kind](https://kind.sigs.k8s.io/) 
(Kubernetes in Docker) allow you to get a Kubernetes cluster with a single command.

#### Technical 101

Whether you’re installing Kubernetes locally on Docker, spinning up and provisioning new virtual 
machines, or preparing new physical servers, you’re going to need a tool to handle all the 
preparation of various Kubernetes components (unless you’re looking to do it the 
[hard way](https://github.com/kelseyhightower/kubernetes-the-hard-way)).

Kubernetes installers simplify that process. Some handle spinning up nodes and others merely 
configure nodes you’ve already provisioned. They all offer various levels of automation and each 
suits different use cases. When getting started with an installer, start by understanding your 
needs, then pick an installer that addresses them. At the time of this writing, kubeadm is 
considered so fundamental to the Kubernetes ecosystem that it’s included as part of the CKA, 
certified Kubernetes administrator exam. Minikube, kind, kops, and kubespray are all CNCF-owned 
Kubernetes installer projects.

</section>

<section data-subcategory="PaaS/Container Service"
         data-buzzwords="">

#### 它是什么

A Platform-as-a-Service, or PaaS, is an environment that allows users to run applications 
without necessarily concerning themselves with the details of the underlying compute resources. 
PaaS and container services in this category are mechanisms to either host a PaaS for developers 
or host services they can use.

#### 它解决什么问题  

We’ve talked a lot about the tools and technologies around cloud native. A PaaS attempts to 
connect many of the technologies found in this landscape in a way that provides direct value 
to developers. It answers the following questions: how will I run applications in various 
environments? And, once running, how will my team and users interact with them?

#### 它如何帮助（解决问题）

PaaS provides opinions and choices around how to piece together the various open and closed 
source tools needed to run applications. Many offerings include tools that handle PaaS installation 
and upgrades and the mechanisms to convert application code into a running application. 
Additionally, PaaS handles the runtime needs of application instances, including on-demand 
scaling of individual components and visibility into the performance and log messages of 
individual apps.

#### Technical 101

Organizations are adopting cloud native technologies to achieve specific business or 
organizational objectives. A PaaS provides a quicker path to value than building a custom 
application platform. Tools like Cloud Foundry Application Runtime help organizations get up 
and running with new applications quickly. They excel at providing the tools needed to 
run [12 factor](https://12factor.net/) or cloud native applications.

Any PaaS comes with its own set of trade-offs and restrictions. Most only work with a subset of 
languages or application types and the opinions and decisions baked into these platforms may or 
may not be a good fit for your needs. Stateless applications tend to do very well in a PaaS but 
stateful applications like databases usually don’t. There are currently no CNCF projects in this 
space but most of the offerings are open source and Cloud Foundry is managed by the Cloud Foundry 
Foundation.

</section>

### Summary: Platform

As we've seen there are multiple tools that help ease Kubernetes adoption. From Kubernetes 
distributions and hosted Kubernetes to more barebones installers or PaaS, they all take various 
installation and configuration burdens and pre-package them for you. Each solution comes with its 
own "flavor." Vendor opinions about what's important and appropriate are built into the solution.

Before adopting any of these, you'll need to do some research to identify the best solution for 
your particular use case. Will you likely encounter advanced Kubernetes scenarios where you'll need 
control over the control plane? If so, hosted solutions may not be a good fit. Do you have a small 
team that manages "standard" workloads and needs to offload as many operational tasks as possible? 
There are multiple aspects to consider. While there is no single best tool for all use cases, 
there certainly will be an optimal tool for your needs. 

## Summary: Cloud Native Landscape

Now that we've broken the CNCF Cloud Native Landscape down and discussed it layer by layer, 
category by category, it probably feels less overwhelming. There is a logical structure to it and, 
once you understand it, navigating the landscape becomes a lot easier. 

The layers of the CNCF Landscape build on each other. First, there is the **provisioning** layer 
with the tools needed to lay the infrastructure foundation. Next is the **runtime** layer where 
everything revolves around containers and what they need to run in a cloud native environment. 
The **orchestration and management** layer contains the tools to orchestrate and manage your 
containers and applications — in other words, the tools needed to create the platform on which 
applications are built. The **application and definition** layer is concerned with the tooling 
needed to enable applications to store and send data as well as with the ways we build and 
deploy our applications. 

Next to the layers, there are two columns. The **observability and analysis** column includes 
tools that monitor applications and flag when something is wrong. Since all layers have to be 
monitored, this category runs across all of them. And finally, there are **platforms**. Platforms 
don't provide new functionality, instead, they bundle multiple tools across the different layers 
together, configuring and fine-tuning them so they are ready to be used. This eases the adoption of 
cloud native technologies and may even be the only way organizations are able to leverage them. 

This concludes the CNCF Landscape guide. We hope you enjoyed the read and that we were able to 
bring a little more clarity to the landscape.

> ##### NOTE
> 
> The cloud native space evolves quickly. If you see anything that's outdated, please submit a PR 
> so we can update it. We want this to be a living document and appreciate your contribution.
