```julia
function rescale!(X::Matrix{T},	bounds::Tuple=(-1, 1);
		dims::Int=1) where T<:Real
```

Rescale the columns or the rows of real matrix `X` to be in range [a, b], where a and b are the first and seconf elements of tuple `bounds`.

By default it applies to the columns. Use `dims=2` for rescaling the rows.

This function is used for normalizing tangent space (feature) vectors. Typically, you won't need it. When fitting a model with [`fit`](@ref)  or performing a cross-validation with [`crval`](@ref), you can simply pass `bounds` to the argument `rescale` of these functions.
