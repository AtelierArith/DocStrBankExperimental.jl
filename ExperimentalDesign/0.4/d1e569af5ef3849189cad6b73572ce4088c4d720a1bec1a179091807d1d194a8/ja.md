```julia
explicit_fullfactorial(factors::Tuple) -> Any

```

カテゴリカル因子レベルを表す配列のタプルを受け取り、明示的なフルファクタリアルデザインを計算します。生成される配列は指数的に大きくなります。

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
