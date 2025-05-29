```
bo!(problem::BossProblem{Function}; kwargs...)
x = bo!(problem::BossProblem{Missing}; kwargs...)
```

与えられた最適化問題を解決するためにベイズ最適化手続きを実行するか、`problem.f == missing` の場合は次の評価ポイントの推奨を行います。

# 引数

  * `problem::BossProblem`: 最適化問題を定義します。

# キーワード

  * `model_fitter::ModelFitter`: モデルパラメータを推定するために使用されるアルゴリズムを定義します。
  * `acq_maximizer::AcquisitionMaximizer`: 取得関数を最大化するために使用されるアルゴリズムを定義します。
  * `acquisition::AcquisitionFunction`: さらなる評価のために有望な候補を選択するために最大化される取得関数を定義します。
  * `term_cond::TermCond`: 終了条件を定義します。
  * `options::BossOptions`: 雑多な設定を定義します。

# 参考文献

[`BossProblem`](@ref), [`ModelFitter`](@ref), [`AcquisitionMaximizer`](@ref), [`TermCond`](@ref), [`BossOptions`](@ref)

# 例

使用例については 'https://soldasim.github.io/BOSS.jl/stable/example/' を参照してください。
