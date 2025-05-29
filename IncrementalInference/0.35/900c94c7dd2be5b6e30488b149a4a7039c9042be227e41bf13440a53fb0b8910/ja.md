```julia
localProduct(dfg, sym; solveKey, N, dbg, logger)

```

因子グラフオブジェクト `dfg` を使用して、接続された因子を通じて信念を変数 `sym` に投影し（尤度との畳み込み）、その後近似的な関数積を行います。

返すもの: 積信念、完全な提案、部分的次元提案、ラベル
