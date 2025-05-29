```
NCMSolution(x, resid, alg, iters, solver, stats)
```

NCM問題を定義する`NCMProblem`の解の表現

## フィールド

  * `X`: NCM問題の解。
  * `resid`: ソルバーの残差。
  * `alg`: ソルバーによって使用されるアルゴリズム。
  * `iters`: NCM問題を解くために使用された反復回数。
  * `solver`: ソルバーの内部キャッシュ変数を含む`NCMSolver`オブジェクト。
  * `stats`: ソルバーの統計。
