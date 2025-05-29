```
DeMatosPruningAlgo <: AbstractCutPruningAlgo
```

信頼度が低いカットを削除します。信頼度はカットに関連付けられたポイント `x` の数です。関連付けられたポイントが多いほど、信頼度は高くなります。

詳細については[1]を参照してください。

[1] De Matos, Vitor L., Andy B. Philpott, and Erlon C. Finardi. "Improving the performance of stochastic dual dynamic programming." Journal of Computational and Applied Mathematics 290 (2015): 196-208.
