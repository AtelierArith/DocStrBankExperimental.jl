```
translate(m1, x) where {T1,D}
```

`m1`の展開点を`x`だけ移動します。

# 引数

  * `m1::Union{AbstractArray{TPS{T1,D}},TPS}`  – 移動する`TPS`または`TPS`マップ
  * `x::Union{Number,AbstractArray{<:Number}}` – 各変数の展開点を移動する量
