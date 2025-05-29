```
mj_applyFT(m, d, force, torque, point, body, qfrc_target)
```

カートesian力とトルクを適用します（xfrc_appliedメカニズムの外部）。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`force::Vector{Float64}`** -> サイズ3のベクトル。`force`はサイズ3のベクトルである必要があります。定数。
  * **`torque::Vector{Float64}`** -> サイズ3のベクトル。`torque`はサイズ3のベクトルである必要があります。定数。
  * **`point::Vector{Float64}`** -> サイズ3のベクトル。`point`はサイズ3のベクトルである必要があります。定数。
  * **`body::Int32`**
  * **`qfrc_target::Vector{Float64}`** -> 可変サイズのベクトル。`qfrc_target`はベクトルである必要があり、行列ではありません。`qfrc_target`はサイズnvである必要があります。
