```
batch_sequence(seqs; pad = 0)
```

Take a list of `N` sequences `seqs`,  where the `i`-th sequence is an array with last dimension `Li`, and turn the into a single array with size `(..., Lmax, N)`.

The sequences need to have the same size, except for the last dimension.

Short sequences will be padded by `pad`.

See also [`batch`](@ref).

# Examples

```jldoctest
julia> batch_sequence([[1, 2, 3], [10, 20]])
3×2 Matrix{Int64}:
 1  10
 2  20
 3   0

julia> seqs = (ones(2, 3), fill(2.0, (2, 5)))
([1.0 1.0 1.0; 1.0 1.0 1.0], [2.0 2.0 … 2.0 2.0; 2.0 2.0 … 2.0 2.0])

julia> batch_sequence(seqs, pad=-1)
2×5×2 Array{Float64, 3}:
[:, :, 1] =
 1.0  1.0  1.0  -1.0  -1.0
 1.0  1.0  1.0  -1.0  -1.0

[:, :, 2] =
 2.0  2.0  2.0  2.0  2.0
 2.0  2.0  2.0  2.0  2.0
```
