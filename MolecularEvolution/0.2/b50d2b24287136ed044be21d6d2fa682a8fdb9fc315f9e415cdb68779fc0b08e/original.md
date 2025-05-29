```
backward!(dest::Partition, source::Partition, model::BranchModel, node::FelNode)
```

Propagate the source partition backwards along the branch to the destination partition, under the model. Note: You should overload this for your own BranchModel types.
