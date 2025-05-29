```
Problem(targets [; cost, penalty, references, reference_mass])
```

Default constructor of a MuSink problem.

The arguments `targets` and `references` are expected to be of type `Dict{Node, Array{Float64, 3}}`, assigning target and reference measures to each node of the tree. If a `reference_mass` is specified, the references will be scaled such that their product measure has mass `reference_mass`.
