```
nodf(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork,BipartiteQuantitativeNetwork}}
```

ネットワークのマージンに対する `nodf` を返します。`i` 引数は、トップレベルの場合は 1、ボトムレベルの場合は 2 に設定でき、無効な値が使用された場合は `ArgumentError` がスローされます。定量的ネットワークの場合は、*WNODF* が使用されます。

#### 参考文献

Almeida-Neto, M., Guimarães, P.R., Loyola, R.D., Ulrich, W., 2008. 生態系におけるネスト性分析のための一貫した指標：概念と測定の調和。Oikos 117, 1227–1239. https://doi.org/10.1111/j.0030-1299.2008.16644.x

Almeida-Neto, M., Ulrich, W., 2011. 定量的行列を使用したネスト性を測定するための簡単な計算アプローチ。Environmental Modelling & Software 26, 173–178. https://doi.org/10.1016/j.envsoft.2010.08.003
