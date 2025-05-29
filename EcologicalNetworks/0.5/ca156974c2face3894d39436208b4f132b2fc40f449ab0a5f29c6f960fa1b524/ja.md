```
degree(N::AbstractEcologicalNetwork; dims::Union{Nothing,Integer}=nothing)
```

ネットワーク内のノードの次数を返します。`dims`は、出次数の場合は`1`、入次数の場合は`2`に設定できます。

#### 参考文献

Delmas, E., Besson, M., Brice, M.-H., Burkle, L.A., Dalla Riva, G.V., Fortin, M.-J., Gravel, D., Guimarães, P.R., Hembry, D.H., Newman, E.A., Olesen, J.M., Pires, M.M., Yeakel, J.D., Poisot, T., 2018. 生態系の相互作用ネットワークの分析。Biological Reviews 112540. https://doi.org/10.1111/brv.12433

Poisot, T., Cirtwill, A.R., Cazelles, K., Gravel, D., Fortin, M.-J., Stouffer, D.B., 2016. 確率的ネットワークの構造。Methods in Ecology and Evolution 7, 303–312. https://doi.org/10.1111/2041-210X.12468

Williams, R.J., 2011. 生物学、方法論、または偶然？二部生態ネットワークの次数分布。PLoS One 6, e17645. https://doi.org/10.1371/journal.pone.0017645
