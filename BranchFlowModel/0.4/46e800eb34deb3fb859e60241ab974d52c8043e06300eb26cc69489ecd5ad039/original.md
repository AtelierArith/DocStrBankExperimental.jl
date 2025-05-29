```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Dict{Int64, Function}, tols::Vector{T}; α::T=0.5, verbose=false) where T <: Real
```

Given a MetaGraphsNext.MetaGraph and a JuMP Model `builder` method iteratively solve the models until the `tols` are met for the differences provided by `BranchFlowModel.get_diffs`. The `builder` dict is used to build each model for the corresponding vertex key.

Each function in the `builder` dict must accept only one argument of type `CommonOPF.AbstractNetwork` that returns a `JuMP.AbstractModel`. Each model returned from the builder function is stored as an `:m` property in each vertex of `mg`.

!!! note
    The `tols` should have a length of three. The first value is compared to the maximum absolute difference in real power, the second for reactive power, and the third for |v|. All differences are calculated at the leaf/substation connections.

