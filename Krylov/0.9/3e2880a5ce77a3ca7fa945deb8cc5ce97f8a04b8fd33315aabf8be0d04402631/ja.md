BICGSTABのインプレースバージョンに必要なベクトルを格納するための型。

外部コンストラクタ

```
solver = BicgstabSolver(m, n, S)
solver = BicgstabSolver(A, b)
solver = BicgstabSolver(kc::KrylovConstructor)
```

を使用して、これらのベクトルを作成することができます。
