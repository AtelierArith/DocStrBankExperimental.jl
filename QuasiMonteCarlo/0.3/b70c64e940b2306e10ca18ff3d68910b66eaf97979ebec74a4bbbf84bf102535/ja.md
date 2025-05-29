```julia
OwenScramble <: ScrambleMethod
```

ネストされた一様スクランブル、別名オーウェンのスクランブル。

`randomize(x, R::OwenScramble)` は `x` のスクランブルされたバージョンを返します。スクランブル手法はネストされた一様スクランブルで、Owen (1995) で導入されました。`pad` は各ポイントに使用されるビット数です。`pad ≥ log(base, n)` が必要です。

参考文献: Owen, A. B. (1995). Randomly permuted (t, m, s)-nets and (t, s)-sequences. In Monte Carlo and Quasi-Monte Carlo Methods in Scientific Computing: Proceedings of a conference at the University of Nevada, Las Vegas, Nevada, USA, June 23–25, 1994 (pp. 299-317). Springer New York.
