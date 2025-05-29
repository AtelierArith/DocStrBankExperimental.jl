```
solve(mme::MME,df::DataFrame;solver="default",printout_frequency=100,tolerance = 0.000001,maxiter = 5000)
```

  * マーカー情報なしで分散成分を推定せずに混合モデル方程式を解きます。

利用可能なソルバーには `default`、`Jacobi`、`Gauss-Seidel`、および `Gibbs sampler` が含まれます。
