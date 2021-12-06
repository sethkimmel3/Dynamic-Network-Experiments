### Problem Statement

WebRTC is an open-source set of protocols and API's which allows developers to enable users to share directional streams of audio, video, and other arbitrary data in real-time. It is built into nearly all modern web browsers, and plays a critical role in important applications for remote work, play, and learning. 

WebRTC is built as a peer-to-peer protocol meaning it is simple to build applications where two users share a bi-directional stream without a centralized server. However, most useful applications of WebRTC involve multi-party communication. For example, video conferencing as well as broadcasting applications necessitate many-to-many, or one-to-many streaming. To enable this requires one of several well-known architectures. In general, there are four options for accomplishing this, well outlined here: [https://webrtcforthecurious.com/docs/08-applied-webrtc/](https://webrtcforthecurious.com/docs/08-applied-webrtc/). To quickly reiterate, they are: 
1) Mesh Networks: These resemble a complete graph, where all users are directly connected to all other users. 
2) Hybrid Mesh Networks: All users are indirectly connected to all other users in some way, but every user is not directly connected to every other user. This resembles a connected graph, but not a complete one.
3) Selective Forwarding Unit (SFU): All users upload media to a central server, and the media is appropriately "forwarded" to the other peers as individual streams.
4) Multi-Point Conferencing Unit (MCU): All users upload media to a central server which is then decoded, stiched together, then redistributed back to peers as one stream.

Hence, the first two methods are "decentralized" (no central server involved), and the third and fourth and "centralized" (involving a central server). Without delving too deep into specifics, each has its own tradeoffs and specific applications favor the use of one or another.

Recently, with the Covid-19 pandemic there has been a a shift to and focus on remote-first, real-time technologies. Even more recently, the so-called "metaverse" has become a widely discussed eventuality of real-time technologies, a virtual world where users can work, play, and learn. The most common parallel drawn is to the sci-fi world of *Ready Player One*. 

Alongside these advances are discussions of ownership within the metaverse and ideas of decentralization. Would it be fair for one or several large corporations (or governments) to own, control, and govern this digital landscape? Should instead it be designed like the world wide web, where users agree on protocols/specs and serve data/content to one another with no central nodes controlling the system? 

The possibility of the latter case would appear unlikely with the current state of efficient WebRTC topologies and other general real-time communication systems. As it currently stands, such an application would likely require a sufficiently powerful MCU, or set of MCU's centrally hosted by to allow a large multi-party session. 

But would it be possible to design a decentralized or psuedo-decentralized (no single point of failure), and network topology with the scale and stability of centalized alternatives? Moreover, is it possible to design one that is (effectively) infinitely scalable like the world wide web itself? 

### Potential Solutions

- One design that immediately jumps out would be a full optimization of the hybrid mesh network, minimizing latency and maximizing fault tolerance. Theoretically, with adequate knowledge of the network structure and bandwidth/compute capacity of the nodes, there should be an optimal node, or set of nodes through which to connect to the network.  
- Each node would keep track of the network structure, but no node is considered to be the source of truth. Upon node connections and disconnections, remaining nodes would propogate information through the network of the change. With some cadence, it may also be worth verifying the entire structure of the network (if possible) with adjacent nodes, seeking consensus so as to provide the most-up-to-date information for joining nodes. If consensus is reached that the network has become unoptimized to a significant extent, there should be a mechanism for mututally-agreed reorganization of the nodes.
- Information of the current network structure would be delivered to the node seeking to join, and it would be up to the joining node to compute the optimal insertion point(s) and make requests to those peers. If the structure has changed, peers in the network reserve the right to refuse insertion to maintain integrity of the network. They would transmit the updated structure back to the requesting node to re-compute optimal insertion point(s). 
- Many individual nodes would act as SFU's or MCU's to most efficiently relay and compress media streaming through the network. 
- For many or most large cases, nodes would not be receiving data from every other node. The determination of which streams would be sent and received would depend on the application. For example, if users were in a 3-d world, it would only be important to receive streams from peers located close by in the world. Like the real world, you may be able to see and hear people within your home, school, or office, but you cannot see or hear people in a building in the next town. 
- In the same vein, nodes may only need to keep track of the local network structure, and potentially some macro-features of the network. More powerful nodes in the network may be tasked with reorganizing the macro-structure of the network if/when necessary.

### Next Step(s)

It's worth clarifying that this would simply be an attempt to improve the state of the art of hybrid mesh networks so as to enable large-scale, decentralized real-time applications. The next thing to do would be to develop a set of graph algorithms for optimal insertion, removal, consensus, and re-organization of a network with respect to latency and fault tolerance. After that, running random simulations on various sized cases should be performed to ensure reliability of the algorithms. 

This problem is loosely coupled, or entirely decoupled from many other important considerations pertaining to the creation of an actual metaverse application. Notions of security, for example, are not currently included here.

On a final note, it's worth stating that while WebRTC is used as the de-facto real-time protocols of the internet right now, that itself may change, and it may not be suitable for such large-scale applications. It's possible that another set of a communication protocols would be used to actually transmit data through the network. 