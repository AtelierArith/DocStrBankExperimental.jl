```
calibrate!(
    node::NetworkNode, climate::Climate, calib_data::DataFrame,
    metric::Union{C,AbstractDict{String,C}};
    kwargs...
) where {C}
```

与えられたノードをBlackBoxOptimパッケージを使用してキャリブレーションします。

# 引数

  * `node::NetworkNode` : ストリームフォールノード
  * `climate` : 気候データ
  * `calib_data` : 対象ノードのキャリブレーションデータで、列名はノード名を示します
  * `metric::Function` : 使用する最適化関数。
