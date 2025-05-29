```
IntervalMatrixPower{T}
```

インクリメント可能な行列の累乗のラッパーです。

### フィールド

  * `M`  – 元の行列
  * `Mᵏ` – 現在の行列の累乗、すなわち $M^k$
  * `k`  – 現在の累乗インデックス

### 注意事項

ラッパーにはインターフェース関数を使用してのみアクセスするべきです。内部表現（フィールドなど）は将来的に変更される可能性があります。

### 例

```jldoctest
julia> A = IntervalMatrix([interval(2, 2) interval(2, 3); interval(0, 0) interval(-1, 1)])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [2.0, 2.0]   [2.0, 3.0]
 [0.0, 0.0]  [-1.0, 1.0]

julia> pow = IntervalMatrixPower(A);

julia> increment!(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [4.0, 4.0]  [2.0, 9.0]
 [0.0, 0.0]  [0.0, 1.0]

julia> increment(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [8.0, 8.0]  [-1.0, 21.0]
 [0.0, 0.0]  [-1.0, 1.0]

julia> matrix(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [4.0, 4.0]  [2.0, 9.0]
 [0.0, 0.0]  [0.0, 1.0]

julia> index(pow)
2

julia> base(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [2.0, 2.0]   [2.0, 3.0]
 [0.0, 0.0]  [-1.0, 1.0]

```
