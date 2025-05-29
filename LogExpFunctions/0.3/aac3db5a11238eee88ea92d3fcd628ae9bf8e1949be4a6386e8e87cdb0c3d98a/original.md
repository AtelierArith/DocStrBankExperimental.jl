```
softmax!(r::AbstractArray{<:Real}, x::AbstractArray{<:Real}=r; dims=:)
```

Overwrite `r` with the [softmax transformation](https://en.wikipedia.org/wiki/Softmax_function) of `x` over dimension `dims`.

That is, `r` is overwritten with `exp.(x)`, normalized to sum to 1 over the given dimensions.

See also: [`softmax`](@ref)
