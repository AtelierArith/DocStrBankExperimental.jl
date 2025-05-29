```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Function, tol::T; α::T=0.5, verbose=false) where T <: Real
```

Given a MetaGraphsNext.MetaGraph and a JuMP Model `builder` method iteratively solve the models until the `tol` is met for the differences provided by `BranchFlowModel.get_diffs`. 

The `builder` must accept only one argument of type `CommonOPF.AbstractNetwork` that returns  a `JuMP.AbstractModel`. Each model returned from the `builder` is stored as an `:m` property in  each vertex of `mg`.

!!! note
    `tol` is compared to the maximum absolute value of all the p, q, and v differences.

