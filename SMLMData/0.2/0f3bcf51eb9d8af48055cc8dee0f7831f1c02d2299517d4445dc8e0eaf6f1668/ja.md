```
BasicSMLD(emitters::Vector{E}, camera::AbstractCamera,
          n_frames::Int, n_datasets::Int,
          metadata::Dict{String,Any}=Dict{String,Any}()) where E<:AbstractEmitter
```

ベクトルのエミッターと必要なメタデータからBasicSMLDを構築します。

# 引数

  * `emitters::Vector{E}`: ローカライズされたエミッターのベクトル
  * `camera::AbstractCamera`: 取得に使用されるカメラ
  * `n_frames::Int`: 取得におけるフレームの総数
  * `n_datasets::Int`: 取得におけるデータセットの数
  * `metadata::Dict{String,Any}=Dict{String,Any}()`: オプションの追加情報

数値型Tはカメラのピクセル*エッジ*x型から推測されます。

# 例

```julia
# 最小限のメタデータで作成
data = BasicSMLD(emitters, camera, 10, 1)

# 追加のメタデータで作成
data = BasicSMLD(emitters, camera, 10, 1, Dict(
    "exposure_time" => 0.1,
    "timestamp" => now()
))
```
