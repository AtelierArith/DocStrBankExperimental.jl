```julia
explicit_fullfactorial(factors::Tuple) -> Any

```

Receives a tuple of arrays  representing categorical factor levels, and computes an explicit full factorial design. The generated array is exponentially large.

```jldoctest
julia> explicit_fullfactorial(([-1, 1], [:a, :b, :c], [1, 2]))
12×3 Matrix{Any}:
 -1  :a  1
  1  :a  1
 -1  :b  1
  1  :b  1
 -1  :c  1
  1  :c  1
 -1  :a  2
  1  :a  2
 -1  :b  2
  1  :b  2
 -1  :c  2
  1  :c  2

```
