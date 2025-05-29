```
primitive_root(FF::Type{<:GaloisFields.AbstractGaloisField})::GaloisFields.AbstractGaloisField
```

有限体の原始根を見つけます。

# 引数

  * `FF::Type{<:GaloisFields.AbstractGaloisField}`: 有限体の型

# 戻り値

  * 有限体の原始根

# 注意事項

  * 原始根は、体の乗法群を生成する要素です
  * 有限体の乗法群は巡回的です

# 例

```julia
F4, α = GaloisField(2, 2, :α)
primitive_root(F4) == α

GF2 = GaloisField(2)
primitive_root(GF2) == GF2(1)
```
