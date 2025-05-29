```
softmax(x::AbstractArray{<:Real}; dims=:)
```

Return the [softmax transformation](https://en.wikipedia.org/wiki/Softmax_function) of `x` over dimension `dims`.

That is, return `exp.(x)`, normalized to sum to 1 over the given dimensions.

See also: [`softmax!`](@ref)
