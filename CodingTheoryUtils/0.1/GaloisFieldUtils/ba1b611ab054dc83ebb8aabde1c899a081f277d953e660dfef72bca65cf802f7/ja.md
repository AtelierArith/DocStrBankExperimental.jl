```
is_primitive(a::GaloisFields.AbstractGaloisField)::Bool
```

要素が有限体の原始根であるかどうかを確認します。

# 引数

  * `a::GaloisFields.AbstractGaloisField`: 有限体の要素

# 戻り値

  * 要素が原始根であれば `true`、そうでなければ `false`

# 注意事項

  * 原始根は、体の乗法群を生成する要素です
  * 有限体の乗法群は巡回群です

# 例

```julia
F4, α = GaloisField(2, 2, :α)
is_primitive(α) == true
is_primitive(F4(1)) == false

GF2 = GaloisField(2)
is_primitive(GF2(1)) == true # GF(2) の特別なケース
```
