```
bayes_rebin_edges(h::Hist1D; prior=BayesHistogram.Geometric(0.995))
```

ヒストグラムの最適なビンエッジをベイズ再ビニングアルゴリズムを使用して見つけます。この関数はエッジのみを見つけ、新しいヒストグラムは返しません。

可能な事前分布については、[`BayesHistogram.jl`](https://github.com/francescoalemanno/BayesHistogram.jl/blob/main/src/BayesHistogram.jl)を参照してください。
