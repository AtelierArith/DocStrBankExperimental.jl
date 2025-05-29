```
mutable struct Alignment{A,T} where {A, T<:Integer}
```

```
    data::Matrix{T}
    alphabet::Union{Nothing, Alphabet{A,T}}
    weights::Vector{Float64} = ones(size(dat,1))/size(dat,1) # phylogenetic weights of sequences
    names::Vector{String} = fill("", size(dat, 1))
```

Biological sequences as vectors of type `T<:Integer`. `data` stores sequences in *columns*: `size(dat)` returns a tuple `(L, M)` with `L` the length and `M` the number of sequences. When displayed, shows `data` as an `MxL` matrix to match with traditional alignments.

`alphabet{A,T}` represents the mapping between integers in `data` and biological symbols of type `A` (nucleotides, amino acids...). If `nothing`, the alignment cannot be mapped to biological sequences.

`weights` represent phylogenetic weights, and are initialized to `1/M`. They must sum to 1. `names` are the label of sequences, and are expected to be in the same order as the columns of `data`. They do not have to be unique, and can be ignored

**Important**: When built from a matrix, assumes that the sequences are stored in *columns*.

## Methods

  * `getindex(X::Alignment, i)` returns a matrix/vector `X.data[:, i]`.
  * `for s in X::Alignment` iterates over sequences.
  * `eachsequence(X::Alignment)` returns an iterator over sequences (`Vector{Int}`).
  * `eachsequence_weighted(X::Alignment)` returns an iterator over sequences and weights as tuples
  * `subaln(X::Alignment, idx)` constructs the subaln defined by index `idx`.
