```
calibrate!(
    sn::StreamfallNetwork,
    v_id::Int64,
    climate::Climate,
    calib_data::DataFrame,
    metric::AbstractDict{String,C};
    kwargs...
) where {C}
```

指定されたノードのみをBlackBoxOptimパッケージを使用してキャリブレーションします。すべての上流ノードはすでにキャリブレーションされていると仮定します。

デフォルトの動作は5分（300秒）間キャリブレーションを行います。

# 引数

  * `sn` : Streamfall Network
  * `v_id` : ノード識別子
  * `climate` : 気候データ
  * `calib_data` : 対象ノードの名前によるキャリブレーションデータ。
  * `metric` : 使用する最適化関数（各ノードのために定義されたもの）。
  * `kwargs` : 追加のキャリブレーション引数。BlackBoxOptimの引数はそのまま渡されます。
