```
remove!(unitCatalogue::UnitCatalogue, name::String)
```

`unitCatalogue`から名前`name`の[`UnitFactorElement`](@ref)オブジェクトを削除します。

# 例外を発生させる

  * `Base.KeyError`: 存在しない要素を削除しようとした場合
