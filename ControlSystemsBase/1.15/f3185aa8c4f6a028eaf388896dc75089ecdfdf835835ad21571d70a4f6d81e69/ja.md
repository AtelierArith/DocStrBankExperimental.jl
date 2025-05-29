```
U = grampd(sys, opt; kwargs...)
```

システム `sys` のグラミアンのコレスキー因子 `U` を返します。`opt` が `:c` の場合、制御可能性グラミアン `G = U*U'` を計算します。`opt` が `:o` の場合、可観測性グラミアン `G = U'U` を計算します。

可観測性グラミアンのために `Cholesky(U)` によって `Cholesky` オブジェクトを取得します。

`MatrixEquations.plyapc/plyapd` を使用します。キーワード引数については、`ControlSystemsBase.MatrixEquations.plyapc/plyapd` のドキュメントを参照してください。
