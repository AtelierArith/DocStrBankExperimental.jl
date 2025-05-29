```
IntervalMatrix{T, IT, MT<:AbstractMatrix{IT}} <: AbstractIntervalMatrix{IT}
```

区間行列、すなわち係数が区間である行列。このタイプは数体、区間タイプ、および行列タイプでパラメータ化されています。

### フィールド

  * `mat` – エントリが区間である行列

### 例

```jldoctest
julia> A = IntervalMatrix([-1 .. -0.8 0 .. 0; 0 .. 0 -1 .. -0.8])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, -0.7999999]   [0.0, 0.0]
  [0.0, 0.0]         [-1.0, -0.7999999]
```

単位行列に比例する区間行列は、標準ライブラリ `LinearAlgebra` の `UniformScaling` 演算子を使用して構築できます。例えば、

```jldoctest interval_uniform_scaling
julia> using LinearAlgebra

julia> IntervalMatrix(interval(1)*I, 2)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [1.0, 1.0]  [0.0, 0.0]
 [0.0, 0.0]  [1.0, 1.0]
```

列数は第3引数として指定でき、主対角線のエントリのみが指定された $m × n$ 行列を作成します。ここで、$k = \min(m, n)$ です：

```jldoctest interval_uniform_scaling
julia> IntervalMatrix(interval(-1, 1)*I, 2, 3)
2×3 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, 1.0]   [0.0, 0.0]  [0.0, 0.0]
  [0.0, 0.0]  [-1.0, 1.0]  [0.0, 0.0]

julia> IntervalMatrix(interval(-1, 1)*I, 3, 2)
3×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [-1.0, 1.0]   [0.0, 0.0]
  [0.0, 0.0]  [-1.0, 1.0]
  [0.0, 0.0]   [0.0, 0.0]
```

初期化されていない区間行列は `undef` を使用して構築できます：

```jldoctest undef_test
julia> m = IntervalMatrix{Float64}(undef, 2, 2);

julia> typeof(m)
IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}
```

このコンストラクタは、新しい区間行列の行列（`mat`）フィールドに暗黙的に密行列 `Matrix{Float64}` を使用することに注意してください。
