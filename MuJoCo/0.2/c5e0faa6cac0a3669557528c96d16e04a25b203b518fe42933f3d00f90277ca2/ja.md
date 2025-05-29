```
mj_rne(m, d, flg_acc, result)
```

RNE: M(qpos)*qacc + C(qpos,qvel) を計算します; flg_acc=0 は慣性項を除去します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`flg_acc::Int32`**
  * **`result::Vector{Float64}`** -> 可変サイズのベクトル。`result` はベクトルである必要があり、行列ではありません。`result` の長さは nv である必要があります。
