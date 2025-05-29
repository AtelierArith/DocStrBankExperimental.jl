```
uncertainty_exponent(bsn::BasinInfo, integ; precision=1e-3) -> α,e,ε,f_ε
```

この関数は境界の不確実性指数を推定します。これは不確実性次元に関連しています。

[C. Grebogi, S. W. McDonald, E. Ott, J. A. Yorke, 最終状態の感度: 予測可能性への障害, Physics Letters A, 99, 9, 1983]

## 引数

  * `bsn` : 流域の情報を保持する構造体。
  * `integ` : 動的システムのイテレータへのハンドル。

## キーワード引数

  * `precision` 不確実性関数の推定器の分散。
