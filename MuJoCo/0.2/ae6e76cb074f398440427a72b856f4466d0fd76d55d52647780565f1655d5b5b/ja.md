```
mj_jacSubtreeCom(m, d, jacp, body)
```

重心エンドエフェクタヤコビアンを計算します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`jacp::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`jacp`は形状(3, nv)である必要があります。必要ない場合は`nothing`に設定できます。
  * **`body::Int32`**
