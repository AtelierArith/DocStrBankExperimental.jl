```
mj_setState(m, d, state, spec)
```

状態を設定します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`state::Vector{Float64}`** -> 可変サイズのベクトル。`state` はベクトルであるべきで、行列ではありません。`state` のサイズは mj_stateSize(m, spec) と等しくする必要があります。
  * **`spec::Int32`**
