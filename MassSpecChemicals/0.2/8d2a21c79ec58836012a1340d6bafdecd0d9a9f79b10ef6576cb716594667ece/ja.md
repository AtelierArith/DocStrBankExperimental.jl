```
isotopicabundance(chemical::AbstractChemical; ignore_isotopes = false)
isotopicabundance(formula::AbstractString; ignore_isotopes = false)
isotopicabundance(elements::Union{<: Vector, Dictionary}; ignore_isotopes = false)
```

`chemical`、`formula`、元素番号のペアのベクター、または元素を番号にマッピングする辞書の同位体存在比を計算します。
