```
LMPlot(x::Array;lags::Int=50,name::String="時系列")
```

`x`の時系列のプロットを返します。

# 引数

  * `x::Array`: 時系列。

# オプション引数

  * `lags::Int`: 自己相関関数で使用するラグの数。
  * `name::String`: プロットで使用する時系列の名前。

# 出力

  * `pp::Plot`: 2x2のグリッドに4つのプロットが返されます：

      * 最初のプロットは`x`の時系列です。
      * 2番目のプロットは、`autocorrelation_plot`関数を使用した`x`の自己相関関数です。
      * 3番目のプロットは、`periodogram_plot`関数を使用した`x`の周期グラムです。
      * 4番目のプロットは、`variance_plot`関数を使用した`x`の分散プロットです。

# 例

```julia
julia> LMPlot(randn(100))
```
