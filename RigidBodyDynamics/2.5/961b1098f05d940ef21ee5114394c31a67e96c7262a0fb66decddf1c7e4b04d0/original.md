```julia
remove_joint!(
    mechanism,
    joint;
    flipped_joint_map,
    spanning_tree_next_edge
)

```

Remove a joint from the mechanism. Rebuilds the spanning tree if the joint is part of the current spanning tree.

Optionally, the `flipped_joint_map` keyword argument can be used to pass in an associative container that will be populated with a mapping from original joints to flipped joints, if removing `joint` requires rebuilding the spanning tree of `mechanism` and the polarity of some joints needed to be changed in the process.

Also optionally, `spanning_tree_next_edge` can be used to select which joints should become part of the new spanning tree, if rebuilding the spanning tree is required.
