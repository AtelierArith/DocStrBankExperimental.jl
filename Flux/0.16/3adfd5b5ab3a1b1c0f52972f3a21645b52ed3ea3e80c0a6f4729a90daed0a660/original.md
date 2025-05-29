```
orthogonal([rng], size...; gain = 1) -> Array
orthogonal([rng]; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` which is a (semi) orthogonal matrix, as described in [1].

Cannot construct a vector, i.e. `length(size) == 1` is forbidden. For `length(size) > 2`, a `prod(size[1:(end - 1)])` by `size[end]` orthogonal matrix is computed before reshaping it to the original dimensions.

# Examples

```jldoctest; setup = :(using LinearAlgebra)
julia> W = Flux.orthogonal(5, 7);

julia> summary(W)
"5×7 Matrix{Float32}"

julia> W * W' ≈ I(5)
true

julia> W2 = Flux.orthogonal(7, 5);

julia> W2 * W2' ≈ I(7)
false

julia> W2' * W2 ≈ I(5)
true

julia> W3 = Flux.orthogonal(3, 3, 2, 4);

julia> transpose(reshape(W3, :, 4)) * reshape(W3, :, 4) ≈ I(4)
true
```

# References

[1] Saxe, McClelland, Ganguli. "Exact solutions to the nonlinear dynamics of learning in deep linear neural networks", ICLR 2014, https://arxiv.org/abs/1312.6120
