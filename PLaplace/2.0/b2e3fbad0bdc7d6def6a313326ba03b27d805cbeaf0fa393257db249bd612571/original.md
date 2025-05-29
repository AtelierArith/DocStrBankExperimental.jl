```julia
append!(
    A::PLaplace.ErrorData,
    B::PLaplace.ErrorData
) -> Vector{Vector{Float64}}

```

Appends to objects of type [ErrorData](@ref) by appending all elements of B to the elements in A.
