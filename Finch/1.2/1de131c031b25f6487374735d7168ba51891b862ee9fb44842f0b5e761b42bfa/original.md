```
fsprand([rng],[type], M..., p, [rfn])
```

Create a random sparse tensor of size `m` in COO format. There are two cases:     - If `p` is floating point, the probability of any element being nonzero is     independently given by `p` (and hence the expected density of nonzeros is     also `p`).     - If `p` is an integer, exactly `p` nonzeros are distributed uniformly at     random throughout the tensor (and hence the density of nonzeros is exactly     `p / prod(M)`). Nonzero values are sampled from the distribution specified by `rfn` and have the type `type`. The uniform distribution is used in case `rfn` is not specified. The optional `rng` argument specifies a random number generator.

See also: (`sprand`)(https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.sprand)

# Examples

```julia
julia> fsprand(Bool, 3, 3, 0.5)
SparseCOO (false) [1:3,1:3]
├─├─[1, 1]: true
├─├─[3, 1]: true
├─├─[2, 2]: true
├─├─[3, 2]: true
├─├─[3, 3]: true

julia> fsprand(Float64, 2, 2, 2, 0.5)
SparseCOO (0.0) [1:2,1:2,1:2]
├─├─├─[2, 2, 1]: 0.6478553157718558
├─├─├─[1, 1, 2]: 0.996665291437684
├─├─├─[2, 1, 2]: 0.7491940599574348
```
