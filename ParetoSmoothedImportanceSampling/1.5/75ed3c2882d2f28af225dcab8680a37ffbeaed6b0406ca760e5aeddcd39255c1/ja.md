```
psislw(lw, [wcpp, wtrunc])
```

パレート平滑化重要度サンプリング（PSIS）を計算します。

# 引数

  * `lw::AbstractArray`: mセットのnログ重みを含むサイズn x mの配列。長さnの一次元配列を提供することも可能です。
  * `wcpp::Real`: GPDフィット推定に使用されるサンプルの割合（デフォルトは20）。
  * `wtrunc::Float64`: 非常に大きな重みをn^wtruncに切り捨てるための正のパラメータ。Falseまたは0を提供すると切り捨てが無効になります。デフォルト値は3/4です。

# 戻り値

  * `lw_out::AbstractArray`: 平滑化されたログ重み
  * `kss::AbstractArray`: パレート尾指数
