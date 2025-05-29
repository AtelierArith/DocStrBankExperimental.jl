```
AbstractField
```

抽象フィールド。

期待される属性：

  * `values::Array{T,2}`: エンティティ番号でインデックスされた自由度パラメータの配列
  * `dofnums::Array{IT,2}`: エンティティ番号でインデックスされた自由度番号の配列
  * `kind::Matrix{Int8}`: エンティティ番号でインデックスされたブールフラグの配列
  * `ranges::Dict(Int8, UnitRange{IT})`: 自由度の範囲の辞書。

参照： [`@add_Field_fields()`](@ref) 。
