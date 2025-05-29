```julia
explicit_fullfactorial(
    iterator::Base.Iterators.ProductIterator
) -> Any

```

`Base.Iterators.ProductIterator` を受け取り、明示的なフルファクターデザインを計算します。生成される配列は指数的に大きくなります。

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
