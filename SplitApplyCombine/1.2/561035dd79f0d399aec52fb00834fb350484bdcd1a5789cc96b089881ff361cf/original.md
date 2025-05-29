```
innerjoin(lkey, rkey, f, comparison, left, right)
```

Performs a relational-style join operation between iterables `left` and `right`, returning a collection of elements `f(l, r)` for which `comparison(lkey(l), rkey(r))` is `true` where `l ∈ left`, `r ∈ right.`

# Example

```jldoctest
julia> innerjoin(iseven, iseven, tuple, ==, [1,2,3,4], [0,1,2])
6-element Array{Tuple{Int64,Int64},1}:
 (1, 1)
 (2, 0)
 (2, 2)
 (3, 1)
 (4, 0)
 (4, 2)
```
