```
RKC(; eigen_est = nothing)
```

B. P. Sommeijer, L. F. Shampine, J. G. Verwer. RKC: An Explicit Solver for Parabolic PDEs, Journal of Computational and Applied Mathematics, 88(2), pp 315-326, 1998. doi: https://doi.org/10.1016/S0377-0427(97)00219-7

RKC: 安定化された明示法。二次安定化ルンゲ-クッタ法。実固有値に対して高い安定性を示します。

この方法は、次の形式のキーワード引数 `eigen_est` を取ります。

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

ここで `upper_bound` はヤコビ行列のスペクトル半径の推定上限です。`eigen_est` が提供されていない場合、`upper_bound` はべき反復を使用して推定されます。
