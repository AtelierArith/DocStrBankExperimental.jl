```
mj_getState(m, d, state, spec)
```

状態を取得します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`** -> 定数。
  * **`state::Vector{Float64}`** -> 可変サイズのベクトル。`state` はベクトルであるべきで、行列ではありません。`state` のサイズは mj_stateSize(m, spec) に等しい必要があります。
  * **`spec::Int32`**
