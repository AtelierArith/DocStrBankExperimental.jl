```
gcp(X::Array, r;
    loss = GCPLosses.LeastSquares(),
    constraints = default_constraints(loss),
    algorithm = default_algorithm(X, r, loss, constraints),
    init = default_init(X, r, loss, constraints, algorithm))
```

テンソル `X` の近似ランク `r` の CP 分解を、損失関数 `loss` に関して計算し、`CPD` オブジェクトを返します。

キーワード引数:

  * `constraints` : 因子行列 `U = (U[1],...,U[N])` に対する制約の `Tuple`。
  * `algorithm`   : 使用するアルゴリズム

従来の CP は、デフォルトの制約なし（すなわち、`constraints = ()`）でデフォルトの `GCPLosses.LeastSquares()` 損失に対応します。

もし `LossFunctions.jl` パッケージも読み込まれている場合、`loss` はそのパッケージからの損失関数でも構いません。サポートされている損失を確認するには `GCPDecompositions.LossFunctionsExt.SupportedLosses` をチェックしてください。

参照: `CPD`, `GCPLosses`, `GCPConstraints`, `GCPAlgorithms`。
