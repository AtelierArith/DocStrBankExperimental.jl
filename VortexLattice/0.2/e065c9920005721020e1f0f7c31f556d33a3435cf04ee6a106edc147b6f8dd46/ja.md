```
far_field_drag(receiving, sending, reference, symmetric)
```

`receiving`から`sending`によって誘導される抗力をTrefftz平面解析を使用して計算します。

# 引数

  * `receiving`: 受信Trefftzパネルのベクトル（[`TrefftzPanel`](@ref)を参照）
  * `sending`: 送信Trefftzパネルのベクトル（[`TrefftzPanel`](@ref)を参照）
  * `reference`: 参照パラメータ（[`Reference`](@ref)を参照）
  * `symmetric`: 誘導速度を計算する際に`surface`内のパネルの鏡像を使用するかどうかを示すフラグ
