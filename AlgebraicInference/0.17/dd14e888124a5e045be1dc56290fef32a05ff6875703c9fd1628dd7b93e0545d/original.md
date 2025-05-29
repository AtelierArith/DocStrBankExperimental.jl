```
solve(
    problem::InferenceProblem,
    elimination_algorithm::EliminationAlgorithm=MinFill()
    supernode_type::SupernodeType=Node()
    architecture_type::ArchitectureType=ShenoyShafer())
```

Solve an inference problem. This involves several steps:

```
interaction graph
    ↓ elimination algorithm
elimination tree
    ↓ supernode type
join tree
    ↓ architecture type
solution
```

First an elimination agorithm is used to construct an elimination tree from the model's interaction graph. Then, nodes of the elimination tree are merged into supernodes, forming a join (or junction) tree. Finally, a message passing algorithm is used to compute a solution.
