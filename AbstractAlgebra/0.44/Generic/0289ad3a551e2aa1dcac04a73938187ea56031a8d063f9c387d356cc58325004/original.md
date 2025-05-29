```
conj(part::Partition)
```

Return the conjugated partition of `part`, i.e. the partition corresponding to the Young diagram of `part` reflected through the main diagonal.

# Examples

```jldoctest
julia> p = Partition([4,2,1,1,1])
4₁2₁1₃

julia> conj(p)
5₁2₁1₂
```
