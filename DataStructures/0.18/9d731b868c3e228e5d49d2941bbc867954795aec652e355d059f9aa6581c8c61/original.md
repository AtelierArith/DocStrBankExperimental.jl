```
prefixsum(ft::FenwickTree{T}, ind::Integer)
```

Return the cumulative sum from index 1 upto `ind` of the [`FenwickTree`](@ref)

# Examples

```
julia> f = FenwickTree{Int}(6)
julia> inc!(f, 2, 5)
julia> prefixsum(f, 1)
 0
julia> prefixsum(f, 3)
 5
```
