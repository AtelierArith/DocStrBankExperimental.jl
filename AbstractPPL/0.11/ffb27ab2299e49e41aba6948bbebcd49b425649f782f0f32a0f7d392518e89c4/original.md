```
VarName{sym}(optic=identity)
```

A variable identifier for a symbol `sym` and optic `optic`.

The Julia variable in the model corresponding to `sym` can refer to a single value or to a hierarchical array structure of univariate, multivariate or matrix variables. The field `lens` stores the indices requires to access the random variable from the Julia variable indicated by `sym` as a tuple of tuples. Each element of the tuple thereby contains the indices of one optic operation.

`VarName`s can be manually constructed using the `VarName{sym}(optic)` constructor, or from an optic expression through the [`@varname`](@ref) convenience macro.

# Examples

```jldoctest; setup=:(using Accessors)
julia> vn = VarName{:x}(Accessors.IndexLens((Colon(), 1)) ⨟ Accessors.IndexLens((2, )))
x[:, 1][2]

julia> getoptic(vn)
(@o _[Colon(), 1][2])

julia> @varname x[:, 1][1+1]
x[:, 1][2]
```
