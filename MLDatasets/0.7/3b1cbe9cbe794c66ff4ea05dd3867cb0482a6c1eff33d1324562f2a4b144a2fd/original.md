```
KarateClub()
```

The Zachary's karate club dataset originally appeared in Ref [1].

The network contains 34 nodes (members of the karate club). The nodes are connected by 78 undirected and unweighted edges. The edges indicate if the two members interacted outside the club.

The node labels indicate which community or the karate club the member belongs to. The club based labels are as per the original dataset in Ref [1]. The community labels are obtained by modularity-based clustering following Ref [2]. The data is retrieved from Ref [3] and [4]. One node per unique label is used as training data.

# References

[1]: [An Information Flow Model for Conflict and Fission in Small Groups](http://www1.ind.ku.dk/complexLearning/zachary1977.pdf)

[2]: [Semi-supervised Classification with Graph Convolutional Networks](https://arxiv.org/abs/1609.02907)

[3]: [PyTorch Geometric Karate Club Dataset](https://pytorch-geometric.readthedocs.io/en/latest/_modules/torch_geometric/datasets/karate.html#KarateClub)

[4]: [NetworkX Zachary's Karate Club Dataset](https://networkx.org/documentation/stable/_modules/networkx/generators/social.html#karate_club_graph)
