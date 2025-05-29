```
Embedding(in => out; init=randn32)
```

A lookup table that stores embeddings of dimension `out`  for a vocabulary of size `in`, as a trainable matrix.

This layer is often used to store word embeddings and retrieve them using indices.  The input to the layer can be a vocabulary index in `1:in`, an array of indices, or the corresponding [`onehot encoding`](@ref OneHotArrays.onehotbatch).

For indices `x`, the result is of size `(out, size(x)...)`, allowing several batch dimensions. For one-hot `ohx`, the result is of size `(out, size(ohx)[2:end]...)`.

# Examples

```jldoctest
julia> emb = Embedding(26 => 4, init=Flux.identity_init(gain=22))
Embedding(26 => 4)  # 104 parameters

julia> emb(2)  # one column of e.weight (here not random!)
4-element Vector{Float32}:
  0.0
 22.0
  0.0
  0.0

julia> emb([3, 1, 20, 14, 4, 15, 7])  # vocabulary indices, in 1:26
4×7 Matrix{Float32}:
  0.0  22.0  0.0  0.0   0.0  0.0  0.0
  0.0   0.0  0.0  0.0   0.0  0.0  0.0
 22.0   0.0  0.0  0.0   0.0  0.0  0.0
  0.0   0.0  0.0  0.0  22.0  0.0  0.0

julia> ans == emb(Flux.onehotbatch("cat&dog", 'a':'z', 'n'))
true

julia> emb(rand(1:26, (10, 1, 12))) |> size  # three batch dimensions
(4, 10, 1, 12)
```
