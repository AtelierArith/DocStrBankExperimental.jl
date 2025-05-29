```
mj_jacPointAxis(m, d, jacp, jacr, point, axis, body)
```

ポイントの移動エンドエフェクタのヤコビアンと軸の回転ヤコビアンを計算します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`jacp::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`jacp`は形状(3, nv)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`jacr::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`jacr`は形状(3, nv)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`point::Vector{Float64}`** -> サイズ3のベクトル。`point`はサイズ3のベクトルである必要があります。定数。
  * **`axis::Vector{Float64}`** -> サイズ3のベクトル。`axis`はサイズ3のベクトルである必要があります。定数。
  * **`body::Int32`**
