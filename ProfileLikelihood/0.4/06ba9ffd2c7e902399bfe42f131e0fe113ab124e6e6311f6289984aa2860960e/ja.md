```
get_prediction_intervals(q, prof::(Bivariate)ProfileLikelihoodSolution, data;
    q_prototype=isinplace(q, 3) ? nothing : build_q_prototype(q, prof, data), resolution=250)
```

予測関数 `q` の出力に対する予測区間を取得します。`q` がベクトルを返す（またはインプレースで操作する）と仮定します。

# 引数

  * `q`: 予測関数で、形式は `(θ, data)` または `(cache, θ, data)` のいずれかです。前者はアウトオブプレースバージョンで、全ベクトルを返しますが、後者はインプレースバージョンで、出力が `cache` に配置されます。引数 `θ` は、尤度問題で使用されるパラメータ（`prof` から）と同じであり、`data` 引数はこの関数の `data` と同じです。
  * `prof::(Bivariate)ProfileLikelihoodSolution`: プロファイル尤度の結果。
  * `data`: `q` における引数 `data`。

# キーワード引数

  * `q_prototype=isinplace(q, 3) ? nothing : build_q_prototype(q, prof, data)`: `q` の結果のプロトタイプ。`q(θ, data)` バージョンを使用している場合、これは `build_q_prototype` から推測できますが、インプレースバージョンを使用している場合は `build_q_prototype` が必要です。例えば、`q` が `Float64` 型のベクトルを返し、長さが 27 の場合、`q_prototype` は `zeros(27)` になる可能性があります。
  * `resolution::Integer=250`: 各パラメータに対して評価する曲線の数。この値は各パラメータに対して同じになります。`prof isa BivariateProfileLikelihoodSolution` の場合、信頼領域のバウンディングボックス内に `resolution^2` 点が定義され、実際の信頼領域の外にあるすべての点は捨てられます。
  * `parallel=false`: マルチスレッドを使用するかどうか。以下で `q_vals` を構築する際にマルチスレッドが使用されます。

# 出力

4つの値が返されます。順番は次の通りです：

  * `individual_intervals`: 各パラメータに対する `q` の出力の予測区間。
  * `union_intervals`: `individual_intervals` からの個々の予測区間の合併。
  * `q_vals`: 考慮された各パラメータでの `q` の値。出力は `Dict` で、パラメータインデックスが `q` の出力の各列にマッピングされ、`j` 番目の列は `param_ranges[j]` でのパラメータ値に対応します。
  * `param_ranges`: 各予測区間に使用されるパラメータ値。
