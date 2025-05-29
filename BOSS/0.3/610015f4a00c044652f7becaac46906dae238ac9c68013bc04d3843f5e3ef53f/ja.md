```
BossProblem(; kwargs...)
```

BOSSアルゴリズムのための最適化問題全体を定義します。

# 問題定義

```
ある（ノイズのある）ブラックボックス関数 `y = f(x) = f_true(x) + ϵ` があり、ここで `ϵ ~ Normal` です。

私たちは、ブラックボックス関数に関する知識（またはその欠如）を記述するサロゲートモデル `y = model(x) ≈ f_true(x)` を持っています。

私たちは、制約 `f(x) <= y_max` を満たしながら `fitness(f(x))` を最大化するような `x ∈ domain` を見つけたいと考えています。
```

# キーワード

  * `fitness::Fitness`: [`Fitness`](@ref) 関数。
  * `f::Union{Function, Missing}`: 目的のブラックボックス関数。
  * `model::SurrogateModel`: [`SurrogateModel`](@ref)。
  * `data::ExperimentData`: 目的関数評価の初期データ。[`ExperimentDataPrior`](@ref) を参照してください。
  * `domain::Domain`: `x` の [`Domain`](@ref)。
  * `y_max::AbstractVector{<:Real}`: `y` に関する制約。（上記の定義を参照してください。）

参照: [`bo!`](@ref)
