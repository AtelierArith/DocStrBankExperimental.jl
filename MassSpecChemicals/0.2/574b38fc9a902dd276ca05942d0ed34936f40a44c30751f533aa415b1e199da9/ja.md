```
mw(formula::AbstractString, net_charge = 0)
mw(elements::Union{<: Vector{<: Pair}, <: Dictionaries.PairDictionary}, net_charge = 0)
mw(chemical::AbstractChemical)
```

化学式、元素ペアのコレクション、または化学物質の分子量。

分子量は、単一の単一同位体化学物質に対しては分子量または化学式量と呼ばれ、複数の化学物質に対しては加重平均と呼ばれます。
