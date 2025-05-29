```
rescaled_range(x::Array; k::Int = 20)
```

時系列の再スケーリング範囲 (R/S) 統計を計算します。

# 引数

  * `x::Array`: 時系列。

# オプション引数

  * `k::Int`: 時系列の分割数。デフォルトは20です。

# 出力

  * `RS::Array`: 再スケーリング範囲統計。

# 例

```julia
julia> rescaled_range(randn(100))
```
