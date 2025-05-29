```
mj_jacBodyCom(m, d, jacp, jacr, body)
```

ボディの重心エンドエフェクタヤコビアンを計算します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`jacp::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`jacp`は形状(3, nv)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`jacr::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`jacr`は形状(3, nv)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`body::Int32`**
