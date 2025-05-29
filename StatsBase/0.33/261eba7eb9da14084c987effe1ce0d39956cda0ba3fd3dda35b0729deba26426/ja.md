```
tiedrank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

配列の[tied ranking](http://en.wikipedia.org/wiki/Ranking#Fractional_ranking_.28.221_2.5_2.5_4.22_ranking.29)、別名分数または「1 2.5 2.5 4」ランキングを返します。`sort`関数と同じキーワード引数をサポートしています。等しい（*「タイ」*）項目は、序数ランキングの下で割り当てられるはずだったランクの平均を受け取ります（[`ordinalrank`](@ref)を参照）。欠損値にはランク`missing`が割り当てられます。
