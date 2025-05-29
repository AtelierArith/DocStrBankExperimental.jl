```
BasicSMLD{T,E<:AbstractEmitter} <: SMLD
```

単一分子局在データの基本コンテナ。

# フィールド

  * `emitters::Vector{E}`: 局在したエミッタのベクター
  * `camera::AbstractCamera`: 取得に使用されるカメラ
  * `n_frames::Int`: 取得におけるフレームの総数
  * `n_datasets::Int`: 取得におけるデータセットの数
  * `metadata::Dict{String,Any}`: 追加のデータセット情報

# 型パラメータ

  * `T`: 座標の数値型（通常はFloat64）
  * `E`: 具体的なエミッタ型

# 例

```julia
# カメラを作成
cam = IdealCamera(1:512, 1:512, 0.1)

# エミッタをいくつか作成
emitters = [
    Emitter2DFit{Float64}(1.0, 1.0, 1000.0, 10.0, 0.01, 0.01, 50.0, 2.0; frame=1),
    Emitter2DFit{Float64}(5.0, 5.0, 1200.0, 12.0, 0.01, 0.01, 60.0, 2.0; frame=2)
]

# メタデータを作成
metadata = Dict{String,Any}(
    "exposure_time" => 0.1,
    "timestamp" => now(),
    "sample" => "Test Sample"
)

# SMLDオブジェクトを作成
data = BasicSMLD(emitters, cam, 2, 1, metadata)
```
