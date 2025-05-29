```julia
explicit_fullfactorial(
    iterator::Base.Iterators.ProductIterator
) -> Any

```

Receives  a  `Base.Iterators.ProductIterator`  and  computes  an  explicit  full factorial design. The generated array is exponentially large.

```jldoctest
julia> explicit_fullfactorial(fullfactorial(([-1, 1], [:a, :b, :c])))
6×2 Matrix{Any}:
 -1  :a
  1  :a
 -1  :b
  1  :b
 -1  :c
  1  :c

```
