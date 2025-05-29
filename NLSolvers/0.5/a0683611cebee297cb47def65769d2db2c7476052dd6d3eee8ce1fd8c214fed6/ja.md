NEqProblem(residuals)   NEqProblem(residuals, options)

平方方程系の残差関数におけるゼロを見つける数学的問題です。この問題は、使用されるアルゴリズムのタイプに応じた適切な目的タイプ（例えば `NonDiffed`、`OnceDiffed`、...）である `residuals` によって定義されます。

オプションは `options` に格納され、`NEqOptions` 型です。オプションに関する詳細情報は `?NEqOptions` を使用して参照してください。

パッケージ NLSolversAD.jl は、ユーザーが提供するよりも高次の導関数を必要とするアルゴリズムに合わせて問題を自動的に変換する機能を追加します。また、ターゲットの導関数の数に対する AD コンストラクタも追加します。
