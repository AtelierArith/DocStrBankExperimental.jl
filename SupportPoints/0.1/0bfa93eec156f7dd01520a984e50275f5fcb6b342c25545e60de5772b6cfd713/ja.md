```
supportpoints(Y, npt; maxit_grad=1000, tol_mm=1e-4, verbosity=0, rng=Random.default_rng())
```

'd' x 'n' 行列である 'Y' の値の分布を表す 'npt' のサポートポイントのセットを見つけます。特徴は 'Y' の列にあります。サポートポイントは 'd' x 'npt' 行列として返されます。

デフォルトのアルゴリズムは、'maxit*mm' の主要化/最大化反復の後に、'maxit*grad' の勾配降下反復を最大 'maxit*grad' 回行います。
