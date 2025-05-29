```julia
function standardize!(X::Matrix{T}; dims::Int=1) where T<:Real 
```

Standardize the columns or the rows of real matrix `X` so that they have zero mean and unit (uncorrected) standard deviation.

By default it applies to the columns. Use `dims=2` for standardizing the rows.

This function is used for normalizing tangent space (feature) vectors. Typically, you won't need it. When fitting a model with [`fit`](@ref)  or performing a cross-validation with [`crval`](@ref), you can simply pass this function as the `normalize` argument.
