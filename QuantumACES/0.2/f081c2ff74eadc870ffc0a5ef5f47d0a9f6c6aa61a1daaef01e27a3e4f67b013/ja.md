```
AbstractNoiseParameters
```

ノイズパラメータは、サブタイプ `T <: AbstractNoiseParameters` に格納されるべきです。

ノイズモデルは、提供されたゲートに対していくつかの提供されたノイズパラメータに従ってパウリエラー確率を生成する [`init_gate_probabilities`](@ref) のメソッドによって生成されるべきです。

# 必要なフィールド

  * `params::Dict{Symbol, Any}`: ノイズパラメータの辞書。
  * `noise_name::String`: ノイズモデルの名前で、パラメータ設定を暗黙的に説明するべきです。
