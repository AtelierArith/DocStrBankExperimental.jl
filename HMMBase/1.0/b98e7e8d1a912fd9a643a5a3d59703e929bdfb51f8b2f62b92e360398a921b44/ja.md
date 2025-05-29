```
randtransmat([rng,] prior) -> Matrix{Float64}
```

遷移行列を生成します。各行は `prior` からサンプリングされます。prior は、ディリクレ分布のような多変量確率分布でなければなりません。

**引数**

  * `prior::MultivariateDistribution`: 遷移行列の行に対する分布。

**例**

```julia
A = randtransmat(Dirichlet([0.1, 0.1, 0.1]))
```
