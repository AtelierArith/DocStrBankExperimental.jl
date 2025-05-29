```
edf_to_onda_annotations(edf::EDF.File, uuid::UUID)
```

`EDF.File` から ID `uuid` の記録に対する EDF+ 注釈を抽出し、それらを `Onda.Annotation` のベクターとして返します。返される各注釈には、対応する EDF+ 注釈の文字列値を含む `value` フィールドがあります。

`edf` に EDF+ 注釈が見つからない場合、空の `Vector{Annotation}` が返されます。
