```
LikelihoodProblem{N,P,D,L,Θ,S} <: AbstractLikelihoodProblem
```

尤度問題を表す構造体。

# フィールド

  * `problem::P`

関連する `OptimizationProblem`。

  * `data::D`

対数尤度関数で使用される引数 `p`。

  * `log_likelihood_function::L`

形 `ℓ(θ, p)` の対数尤度関数。

  * `θ₀::Θ`

MLE `θ` の初期推定値。

  * `syms::S`

パラメータの変数名。これは `SymbolicIndexingInterface.jl` の `SymbolCache` にラップされています。

追加のパラメータ `N` はパラメータの数です。

# コンストラクタ

## 標準

```
LikelihoodProblem(loglik::Function, θ₀;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    f_kwargs=nothing, prob_kwargs=nothing)
```

[`LikelihoodProblem`](@ref) のコンストラクタ。

### 引数

  * `loglik::Function`: 形 `ℓ(θ, p)` の対数尤度関数。
  * `θ₀`: MLE の推定値。

### キーワード引数

  * `syms=eachindex(θ₀)`: 各パラメータの名前。
  * `data=SciMLBase.NullParameters()`: 対数尤度関数におけるパラメータ `p`。
  * `f_kwargs=nothing`: `OptimizationFunction` に渡される `NamedTuple` としてのキーワード引数。
  * `prob_kwargs=nothing`: `OptimizationProblem` に渡される `NamedTuple` としてのキーワード引数。

### 出力

[`LikelihoodProblem`](@ref) 問題オブジェクトを返します。

## 微分方程式問題の引数付き

```
LikelihoodProblem(loglik::Function, θ₀,
    ode_function, u₀, tspan;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    ode_parameters=SciMLBase.NullParameters(), ode_alg,
    ode_kwargs=nothing, f_kwargs=nothing, prob_kwargs=nothing)
```

微分方程式問題のための [`LikelihoodProblem`](@ref) のコンストラクタ。

### 引数

  * `loglik::Function`: 形 `ℓ(θ, p, integrator)` の対数尤度関数。
  * `θ₀`: MLE の推定値。
  * `ode_function`: 微分方程式のための関数 `f(du, u, p, t)` または `f(u, p, t)`。
  * `u₀`: 微分方程式の初期条件。
  * `tspan`: 微分方程式を解く時間範囲。

### キーワード引数

  * `syms=eachindex(θ₀)`: 各パラメータの名前。
  * `data=SciMLBase.NullParameters()`: 対数尤度関数におけるパラメータ `p`。
  * `ode_parameters=SciMLBase.NullParameters()`: `ode_function` におけるパラメータ `p`。
  * `ode_alg`: 微分方程式を解くために使用されるアルゴリズム。
  * `ode_kwargs=nothing`: 統合器に渡すための `NamedTuple` としての追加のキーワード引数; `construct_integrator` を参照。
  * `f_kwargs=nothing`: `OptimizationFunction` に渡される `NamedTuple` としてのキーワード引数。
  * `prob_kwargs=nothing`: `OptimizationProblem` に渡される `NamedTuple` としてのキーワード引数。

### 出力

[`LikelihoodProblem`](@ref) 問題オブジェクトを返します。

## 統合器付き

```
LikelihoodProblem(loglik::Function, θ₀, integrator;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    f_kwargs=nothing, prob_kwargs=nothing)
```

関連する `integrator` を持つ微分方程式問題のための [`LikelihoodProblem`](@ref) のコンストラクタ。

### 引数

  * `loglik::Function`: 形 `ℓ(θ, p, integrator)` の対数尤度関数。
  * `θ₀`: MLE の推定値。
  * `integrator`: 微分方程式問題のための統合器。`construct_integrator` も参照。

### キーワード引数

  * `syms=eachindex(θ₀)`: 各パラメータの名前。
  * `data=SciMLBase.NullParameters()`: 対数尤度関数におけるパラメータ `p`。
  * `f_kwargs=nothing`: `OptimizationFunction` に渡される `NamedTuple` としてのキーワード引数。
  * `prob_kwargs=nothing`: `OptimizationProblem` に渡される `NamedTuple` としてのキーワード引数。

### 出力

[`LikelihoodProblem`](@ref) 問題オブジェクトを返します。
