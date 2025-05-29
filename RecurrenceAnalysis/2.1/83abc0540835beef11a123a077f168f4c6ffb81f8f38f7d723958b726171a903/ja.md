```
sorteddistances(x; kwargs...)
```

埋め込まれた時系列 `x` の点間のソートされた距離と、それらの値に基づく再発率を含むタプルを返します。

キーワード引数は、これらの結果を得るために `recurrencematrix` および `recurrencerate` 関数に渡すべきものと同じです。すなわち、もし `d,r = sorteddistances(x; kwargs...)` であり、`rmat = recurrencematrix(x, d[i]; kwargs...)` であれば、`recurrencerate(rmat; kwargs...) == r[i]` となります。
