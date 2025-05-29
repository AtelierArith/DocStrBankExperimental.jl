```
weight(bsf::AbstractVecOrMat{Bool}) -> Int
```

Return the weight of the binary symplectic form.

# Examples

```jldoctest
julia> weight(BitVector([1, 0, 0, 0, 1, 0, 0, 1, 0, 1]))
3
```

```jldoctest
julia> weight(BitMatrix([1 0 0 0 1 0 0 1 0 1; 1 1 1 1 1 0 0 0 0 0]))
8
```
