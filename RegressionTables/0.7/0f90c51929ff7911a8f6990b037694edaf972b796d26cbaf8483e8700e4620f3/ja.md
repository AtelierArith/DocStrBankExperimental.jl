出版品質の回帰テーブルを生成します。これは、Stataの`esttab`やRの`stargazer`に似ています。

### 引数

  * `rr::FixedEffectModel...` は、印刷する必要がある `FixedEffectModel` で、`FixedEffectModels.jl` からのものです。必須の引数です。
  * `keep` は、表示する回帰変数名（`String`）、整数、範囲、または正規表現の `Vector` です。デフォルトは空のベクターで、その場合はすべての回帰変数が表示されます。文字列は係数の再ラベル名である必要があります。
  * `drop` は、表示しない回帰変数名（`String`）、整数、範囲、または正規表現の `Vector` です。デフォルトは空のベクターで、その場合は回帰変数は削除されません。文字列は係数の再ラベル名である必要があります。
  * `order` は、表示する回帰変数名（`String`）、整数、範囲、または正規表現の `Vector` で、その順序で表示されます。デフォルトは空のベクターで、その場合は回帰変数の順序は変更されません。他の回帰変数はまだ表示されます（`drop` が空であると仮定します）。文字列は係数の再ラベル名である必要があります。
  * `fixedeffects` は、表示するFE名（`String`）、整数、範囲、または正規表現の `Vector` で、その順序で表示されます。デフォルトは空のベクターで、その場合はすべてのFEが表示されます。
  * `align` は、結果列の整列を示す `Symbol` で、セット `[:l,:c,:r]` から選択します（デフォルトは `:r` 右揃え）。現在、ASCIIおよびLaTeX出力でのみ機能します。
  * `header_align` は、ヘッダー行の整列を示す `Symbol` で、セット `[:l,:c,:r]` から選択します（デフォルトは `:c` 中央揃え）。現在、ASCIIおよびLaTeX出力でのみ機能します。
  * `labels` は、変数（`String`）およびテーブル内の他のテキストの表示ラベルを含む `Dict` です。変数のラベルが見つからない場合、デフォルトは変数名になります。特別な値についてはドキュメントを参照してください。
  * `estimformat` は、推定値の形式を説明する `String` です。
  * `digits` は、推定値に表示される精度を説明する `Int` です。デフォルトは `nothing` で、その場合はデフォルト（3）が使用されます（デフォルトは `RegressionTables.default_digits(render::AbstractRenderType, x) = 3` を設定することで変更できます）。
  * `statisticformat` は、推定値の下に表示される数値の形式を説明する `String` です（se/t）。
  * `digits_stats` は、統計に表示される精度を説明する `Int` です。デフォルトは `nothing` で、その場合はデフォルト（3）が使用されます（デフォルトは `RegressionTables.default_digits(render::AbstractRenderType, x) = 3` を設定することで変更できます）。
  * `below_statistic` は、各点推定値の下に表示される統計を説明する型です。認識される値は `nothing`、`StdError`、`TStat`、および `ConfInt` です。`nothing` は行を抑制します。デフォルトは `StdError` です。
  * `regression_statistics` は、テーブルの下部に表示される統計を説明する型の `Vector` です。組み込みの認識された型は `Nobs`、`R2`、`PseudoR2`、`R2CoxSnell`、`R2Nagelkerke`、`R2Deviance`、`AdjR2`、`AdjPseudoR2`、`AdjR2Deviance`、`DOF`、`LogLikelihood`、`AIC`、`AICC`、`BIC`、`FStat`、`FStatPValue`、`FStatIV`、`FStatIVPValue`、`R2Within` です。デフォルトは回帰入力に基づいて異なります（単純線形モデルは [Nobs, R2] です）。
  * `extralines` は、テーブルの最後に追加される `Vector` または `Vector{<:AbsractVector}` です。単一のベクターは独自の行になります。ベクターのベクターはそれぞれが行になります。デフォルトは `nothing` です。
  * `number_regressions` は、回帰に番号を付けるかどうかを制御する `Bool` です。デフォルトは `true` です。
  * `groups` は、回帰をグループ化するために使用されるラベルの `Vector`、`Vector{<:AbstractVector}` または `Matrix` です。これは、異なるデータセットやサンプル制限の結果を表示する場合に便利です。
  * `print_fe_section` は、固定効果に関するセクションを表示するかどうかを制御する `Bool` です。デフォルトは `true` です。
  * `print_estimator_section` は、どの推定量（OLS/IV/Binomial/Poisson...）が使用されているかに関するセクションを印刷するかどうかを制御する `Bool` です。デフォルトは、表示される値が1つ以上の場合は `true` です。
  * `standardize_coef` は、テーブルが標準化された係数を表示するかどうかを制御する `Bool` です。これは `TableRegressionModel` にのみ機能し、係数の推定値と `below_statistic` のみが標準化されます（すなわち、R^2などは非標準化回帰に関連します）。
  * `render::AbstractRenderType` は、テーブルがどのようにレンダリングされるかを制御する `AbstractRenderType` 型です。標準のサポートされている型は、ASCII（`AsciiTable()` を介して）およびLaTeX（`LatexTable()` を介して）です。デフォルトは `AsciiTable()` です。
  * `file` は、テーブルをファイルに保存するかどうかを制御する `String` です。デフォルトは `nothing` です。
  * `transform_labels` は、`Dict` または `:ampersand`、`:underscore`、`:underscore2space`、`:latex` のいずれかの `Symbol` です。
  * `confint_level` は、信頼区間の信頼レベルを制御する `Float64` です。デフォルトは `0.95` です。

### 詳細

一般的な使用法は、いくつかの `FixedEffectModel` を関数に渡し、どのようにレンダリングするかを指定することです（`render` 引数を使用）：

```julia
regtable(regressionResult1, regressionResult2; render = AsciiTable())
```

`file` 引数に文字列を渡すことで、ファイルを作成または上書きします。たとえば、LaTeX出力を使用する場合、

```julia
regtable(regressionResult1, regressionResult2; render = LatexTable(), file="myoutfile.tex")
```

詳細については、完全な引数リストを参照してください。
