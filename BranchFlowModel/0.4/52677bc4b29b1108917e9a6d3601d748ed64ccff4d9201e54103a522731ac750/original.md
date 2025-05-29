```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Function, tols::Vector{T}; α::T=0.5, verbose=false) where T <: Real
```

Given a MetaGraphsNext.MetaGraph and a JuMP Model `builder` method iteratively solve the models until the `tols` are met for the differences provided by `BranchFlowModel.get_diffs`. 

The `builder` must accept only one argument of type `CommonOPF.AbstractNetwork` that returns  a `JuMP.AbstractModel`. Each model returned from the `builder` is stored as an `:m` property in  each vertex of `mg`.

!!! note
    The `tols` should have a length of three. The first value is compared to the maximum absolute difference in real power, the second for reactive power, and the third for |v|. All differences are calculated at the leaf/substation connections.

