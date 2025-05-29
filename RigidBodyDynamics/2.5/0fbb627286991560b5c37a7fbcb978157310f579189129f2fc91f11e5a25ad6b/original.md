```julia
remove_fixed_tree_joints!(mechanism)

```

Remove any fixed joints present as tree edges in `mechanism` by merging the rigid bodies that these fixed joints join together into bodies with equivalent inertial properties.
