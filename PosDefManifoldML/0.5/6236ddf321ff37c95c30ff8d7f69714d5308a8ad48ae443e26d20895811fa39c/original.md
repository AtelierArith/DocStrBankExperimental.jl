```julia
function normalize!(X::Matrix{T}; dims::Int=1) where T<:Real 
```

Normalize the columns or the rows of real matrix `X` so that their 2-norm divided by their number of elements is 1.0. This way the value of each element of matrix `X` gravitates  around 1.0, regardless its size.

By default it applies to the columns. Use `dims=2` for normlizing the rows.

This function is used for normalizing tangent space (feature) vectors. Typically, you won't need it. When fitting a model with [`fit`](@ref)  or performing a cross-validation with [`crval`](@ref), you can simply pass this function as the `normalize` argument.
