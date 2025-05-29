```
orthogonal([rng], size...; gain = 1) -> Array
orthogonal([rng]; kw...) -> Function
```

与えられた `size` の `Array{Float32}` を返します。これは、[1] に記載されているように (半) 直交行列です。

ベクトルを構築することはできません。すなわち、`length(size) == 1` は禁止されています。`length(size) > 2` の場合、元の次元に再形成する前に、`prod(size[1:(end - 1)])` 行 `size[end]` 列の直交行列が計算されます。

# 例

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

# 参考文献

[1] Saxe, McClelland, Ganguli. "Exact solutions to the nonlinear dynamics of learning in deep linear neural networks", ICLR 2014, https://arxiv.org/abs/1312.6120
