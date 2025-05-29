```
samplesurface(surf::ParametricSurface{T,N}, samplefunction::Function, numsamples::Int = 30)
```

提供された関数を使用して、UV空間の偶数の `numsamples`×`numsamples` グリッド上でパラメトリックサーフェスをサンプリングします。
