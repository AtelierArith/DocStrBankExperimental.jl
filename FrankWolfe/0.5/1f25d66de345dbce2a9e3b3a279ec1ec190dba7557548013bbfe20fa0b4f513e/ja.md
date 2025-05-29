```
away_frank_wolfe(f, grad!, lmo, x0; ...)
```

アウェイステップを用いたフランク・ウォルフ法。アルゴリズムは、[`FrankWolfe.ActiveSet`](@ref) データ構造内の頂点の凸結合として現在の反復値を維持します。アウェイステップの例については、[M. Besançon, A. Carderera and S. Pokutta 2021](https://arxiv.org/abs/2104.06675)を参照してください。
