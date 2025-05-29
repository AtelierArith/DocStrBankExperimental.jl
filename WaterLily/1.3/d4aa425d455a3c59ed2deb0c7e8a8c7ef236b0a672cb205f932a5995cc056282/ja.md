```
MultiLevelPoisson{N,M}
```

圧力ポアソン方程式を[幾何学的多重格子法](https://en.wikipedia.org/wiki/Multigrid_method)で解くために使用される複合型。唯一の変数は`levels`で、ネストされた`Poisson`システムのベクトルです。
