```
eye(N::Int; type=Operator, dims=nothing)
qeye(N::Int; type=Operator, dims=nothing)
```

Identity operator $\hat{\mathbb{1}}$ with size `N`.

It is also possible to specify the list of Hilbert dimensions `dims` if different subsystems are present.

Note that `type` can only be either [`Operator`](@ref) or [`SuperOperator`](@ref)

!!! note
    `qeye` is a synonym of `eye`.

