```
EmbeddingBag(in => out, reduction=mean; init=Flux.randn32)
```

A lookup table that stores embeddings of dimension `out` for a vocabulary of size `in`. Differs from [`Embedding`](@ref) in that, instead of acting on a single vocabulary index, it always acts a vector of indices which it calls a "bag". Their individual embedding vectors are reduced to one, using `mean` or some other function.

Instead of acting on one "bag", such as `x::Vector{Int}`, the layer can also act on several:

  * Acting on a vector of "bags", it produces a matrix whose columns are the reduced vectors. More generally on `x::Array{Vector{Int}}`, its output is of size `(out, size(x)...)`.
  * Any higher-rank array of integers is interpreted as a collection of "bags" each along the first dimension. Thus the output is `mapslices(e, x; dims=1)` when `e::EmbeddingBag` and `x::Array{Int,N}`. This method is more efficient, but requires that all "bags" have the same length.
  * A vector of "bags" may also be produced by splitting a vector of indices at specified points. For this case the layer takes two inputs, both vectors of integers. See details below.

The "bag" may equivalently be represented as a `OneHotMatrix`. A collection of these, or one higher-rank `OneHotArray`, again produce a stack of embeddings. See details below.

# Examples

```jldoctest ebag
julia> vocab_size = 26;  # embed into 3 dimensions, with non-random vectors:

julia> eb = EmbeddingBag(vocab_size => 3, init=Flux.identity_init(gain=100))
EmbeddingBag(26 => 3)  # 78 parameters

julia> eb([2])  # one bag of 1 item
3-element Vector{Float32}:
   0.0
 100.0
   0.0

julia> eb([3,3,1])  # one bag of 3 items, one mean embedding
3-element Vector{Float32}:
 33.333332
  0.0
 66.666664

julia> eb([[3,1,3], [2,1]])  # two bags
3×2 Matrix{Float32}:
 33.3333  50.0
  0.0     50.0
 66.6667   0.0

julia> eb([1 1 1 1; 1 2 3 4])  # 4 bags each of 2 items, eachcol([1 1 1 1; 1 2 3 4])
3×4 Matrix{Float32}:
 100.0  50.0  50.0  50.0
   0.0  50.0   0.0   0.0
   0.0   0.0  50.0   0.0

julia> eb(rand(1:26, 10, 5, 5)) |> size  # 25 bags each of 10 items
(3, 5, 5)
```

Another way to specify "many bags of many items" is to provide a vector `data` (each in `1:in`) and a vector `at` stating where to split that up into "bags". The first bag starts with `data[at[1]]`, the second at `data[at[2]]`, and so on,  with no overlaps and nothing left out (thus it requires `at[1]==1`).

```jldoctest ebag
julia> data = [11, 1, 12, 2, 13, 3, 14];

julia> data[1:3], data[4:end]
([11, 1, 12], [2, 13, 3, 14])

julia> eb(data, [1, 4])  # two bags, of 3 and 4 items
3×2 Matrix{Float32}:
 33.3333   0.0
  0.0     25.0
  0.0     25.0
```

Finally, each bag may also be also be represented as a [`OneHotMatrix`](@ref OneHotArrays.onehotbatch).

```jldoctest ebag
julia> eb(Flux.onehotbatch("bba", 'a':'z'))  # same as [2,2,1], one bag of 3 items
3-element Vector{Float32}:
 33.333332
 66.666664
  0.0

julia> eb([Flux.onehotbatch("bba", 'a':'z'), Flux.onehotbatch("cc", 'a':'z')])  # two bags
3×2 Matrix{Float32}:
 33.3333    0.0
 66.6667    0.0
  0.0     100.0
```
