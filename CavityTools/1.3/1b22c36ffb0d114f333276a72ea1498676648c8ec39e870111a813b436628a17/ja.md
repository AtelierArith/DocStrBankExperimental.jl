`CumSum(a::Accumulator)` は、`a` が更新されるたびに更新されます。更新と取得の時間はどちらも `O(log(length(a)))` です。通常、`cumsum(a)` を使って構築され、時間は `O(1)` です。

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

julia> c = cumsum(a)
CumSum(Accumulator([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]))

julia> c[end]
55

julia> a[1] = 100
100

julia> c[end]
154
```
