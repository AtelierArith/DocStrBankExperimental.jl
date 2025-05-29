```
apply_projection_sign(projection::Projection, sign_matrix::Array{<:Real, 4})
```

投影の符号を投影に適用しました。

# 引数

  * `projection::Projection`: 波動関数の投影
  * `sign_matrix::Array{Integer, 4}`: get*projection*sign 関数から返される符号

# 戻り値

  * `Projection`: 新しい投影
