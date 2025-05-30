```julia
MatousekScramble <: ScrambleMethod
```

線形行列スクランブル、別名マトウセクのスクランブル。

`randomize(x, R::MatousekScramble)` は `x` のスクランブルされたバージョンを返します。スクランブル手法は、Matousek (1998) で導入された線形行列スクランブルです。`pad` は各ポイントに使用されるビット数です。`pad ≥ log(base, n)` が必要です。

参考文献: Matoušek, J. (1998). On thel2-discrepancy for anchored boxes. Journal of Complexity, 14(4), 527-556.
