```
add!(unitCatalogue::UnitCatalogue, unitPrefix::UnitPrefix)
add!(unitCatalogue::UnitCatalogue, baseUnit::BaseUnit)
```

`unitCatalogue`に[`UnitFactorElement`](@ref)を追加します。

追加する要素と同じ名前の要素が`unitCatalogue`に既に存在してはいけません。

# 例外を発生させる

  * `Alicorn.Exceptions.DuplicationError`: 追加する要素と同じ`name`フィールドを持つ[`UnitFactorElement`](@ref)が`unitCatalogue`に既に存在する場合。
