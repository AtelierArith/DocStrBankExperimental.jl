```julia
function demean!(X::Matrix{T}; dims::Int=1) where T<:Real 
```

Remove the mean from the columns or from the rows of real matrix `X`.

By default it applies to the columns. Use `dims=2` for demeaning the rows.

This function is used for normalizing tangent space (feature) vectors. Typically, you won't need it. When fitting a model with [`fit`](@ref)  or performing a cross-validation with [`crval`](@ref), you can simply pass this function as the `normalize` argument.
