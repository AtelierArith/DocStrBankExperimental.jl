```
    findLabels(label::String, ::Vector{DataType} = allNumerals; pfxList=Vector{String}=[""])
        -> Vector{Tuple{LabelNumeral,Type}}}
```

`allNumerals` = [AlphaNumeral, RomanNumeral, Int, LookupNumeral, AlphaNumNumeral] を考慮してください。

入力された `String` に最も適した `LabelNumeral` を見つけます。`pfxList` は1つ以上のラベルプレフィックス値を提供します。

この関数は、すべての一致する `LabelNumeral` と、その内部構成に最も適した数値の `Type` の配列を返します。
