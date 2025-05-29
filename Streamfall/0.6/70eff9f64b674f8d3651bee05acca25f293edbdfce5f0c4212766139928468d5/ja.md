```
calibrate!(
    node::NetworkNode,
    climate::Climate,
    calib_data::AbstractArray,
    metric::Union{C,AbstractDict{String,C}};
    kwargs...
) where {C}
```

与えられたノードをBlackBoxOptimパッケージを使用してキャリブレーションします。

# 引数

  * `node::NetworkNode` : ストリームフォールノード
  * `climate` : 気候データ
  * `calib_data` : 対象ノードのIDによるキャリブレーションデータ
  * `extractor::Function` : キャリブレーション抽出メソッド、動作を変更するためにカスタムのものを定義
  * `metric::Function` : 使用する最適化関数。デフォルトはRMSEです。
