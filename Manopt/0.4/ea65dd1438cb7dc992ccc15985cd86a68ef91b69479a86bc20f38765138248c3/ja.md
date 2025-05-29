```
check_differential(M, F, dF, p=rand(M), X=rand(M; vector_at=p); kwargs...)
```

関数 `F(M,p)` の微分 `dF(M,p,X)` が正しいかどうかを数値的に確認します。

これは[Boumal:2023; Section 4.8](@cite)で説明されている方法を実装しています。

エラーが指定された許容範囲内であり、かつ方法が正確であれば、プロットは生成されません。

# キーワード引数

  * `exactness_tol`:     （`1e-12`）すべてのエラーがこの許容範囲内であれば、微分は正確と見なされます
  * `io`:                （`nothing`）結果を出力するための `IO` を提供します
  * `limits`:            （`(1e-8,1)`）`log_range` の範囲を指定します
  * `log_range`:         （`range(limits[1], limits[2]; length=N)`）微分線をサンプリングするためのポイントの範囲（対数スケール）を指定します
  * `N`:                 （`101`）`log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で確認するポイントの数
  * `name`:              （`"differential"`）プロットに表示する名前
  * `plot`:              （`false`）結果をプロットするかどうか（`Plots.jl` がロードされている場合）。プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `retraction_method`: （`default_retraction_method(M, typeof(p))`）使用する再収束法
  * `slope_tol`:         （`0.1`）近似の傾き（グローバル）の許容範囲
  * `throw_error`:       （`false`）微分が間違っている場合にエラーメッセージを投げる
  * `window`:            （`nothing`）傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用します。
