```
Cora()
```

The Cora citation network dataset from Ref. [1]. Nodes represent documents and edges represent citation links. Each node has a predefined feature with 1433 dimensions.  The dataset is designed for the node classification task.  The task is to predict the category of certain paper. The dataset is retrieved from Ref. [2].

# Statistics

  * Nodes: 2708
  * Edges: 10556
  * Number of Classes: 7
  * Label split:

      * Train:  140
      * Val:    500
      * Test:  1000

The split is the one used in the original paper [1] and  doesn't consider all nodes.

# References

[1]: [Deep Gaussian Embedding of Graphs: Unsupervised Inductive Learning via Ranking](https://arxiv.org/abs/1707.03815)

[2]: [Planetoid](https://github.com/kimiyoung/planetoid)
