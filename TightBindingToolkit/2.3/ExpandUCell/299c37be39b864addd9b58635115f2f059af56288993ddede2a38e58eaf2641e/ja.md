```julia
ExpandBonds!(ucOG::UnitCell{T}, ucNew::UnitCell{T} ; OffsetRange::Int64 = 2)
```

`ucNew`で与えられた新しい原始ベクトルを使用する`ExpandUnitCell`のインプレースバージョンです。
