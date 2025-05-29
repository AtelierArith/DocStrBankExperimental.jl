```
reformat(l::Lineage, ranks::Vector{Symbol})
```

与えられたランクに従って再フォーマットされた `Lineage` オブジェクトを返します。系統に対してランクに対応する分類群がない場合、`UnclassifiedTaxon` が格納されます。一度 `Lineage` が再フォーマットされると、再度再フォーマットすることはできません。
