```julia
ArrayPartition(x::AbstractArray...)
```

An `ArrayPartition` `A` is an array, which is made up of different arrays `A.x`. These index like a single array, but each subarray may have a different type. However, broadcast is overloaded to loop in an efficient manner, meaning that `A .+= 2.+B` is type-stable in its computations, even if `A.x[i]` and `A.x[j]` do not match types. A full array interface is included for completeness, which allows this array type to be used in place of a standard array where such a type stable broadcast may be needed. One example is in heterogeneous differential equations for [DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/).

An `ArrayPartition` acts like a single array. `A[i]` indexes through the first array, then the second, etc., all linearly. But `A.x` is where the arrays are stored. Thus, for:

```julia
using RecursiveArrayTools
A = ArrayPartition(y, z)
```

we would have `A.x[1]==y` and `A.x[2]==z`. Broadcasting like `f.(A)` is efficient.
