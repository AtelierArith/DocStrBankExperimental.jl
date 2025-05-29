`a = Accumulator(v::AbstractVector; op=+, init=zero)` は、`v` の代わりに追加の追跡計算（例えば `sum`）を行うための置き換えとして機能します。`CumSum` と `Cavity` も参照してください。

```
julia> a = Accumulator([1:10;])
10-element Accumulator{Int64, +, zero}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10

julia> sum(a)
55

julia> a[1]=0
0

julia> sum(a)
54

```
