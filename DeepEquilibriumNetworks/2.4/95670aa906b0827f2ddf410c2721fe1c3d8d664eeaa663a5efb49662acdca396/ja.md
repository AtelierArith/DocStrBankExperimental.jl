```
DeepEquilibriumNetwork(model, solver; init = missing, jacobian_regularization=nothing,
    problem_type::Type=SteadyStateProblem{false}, kwargs...)
```

Deep Equilibrium Networkは、[baideep2019](@cite)および[pal2022mixing](@cite)で提案されています。

## 引数

  * `model`: ニューラルネットワーク。
  * `solver`: 根を求める問題のためのソルバー。ODEソルバーと非線形ソルバーの両方がサポートされています。

## キーワード引数

  * `init`: 根を求める問題の初期条件。`nothing`の場合、初期条件は`zero(x)`に設定されます。`missing`の場合、初期条件は`WrappedFunction(zero)`に設定されます。それ以外の場合、初期条件は`init(x, ps, st)`に設定されます。
  * `jacobian_regularization`: `nothing`、`AutoForwardDiff`、`AutoFiniteDiff`、または`AutoZygote`のいずれかでなければなりません。
  * `problem_type`: `problem_type`を`ODEProblem`に設定することで、バニラニューラルODEをシミュレートする方法を提供します。デフォルトでは、問題のタイプは`SteadyStateProblem`に設定されています。
  * `kwargs`: `SciMLBase.solve`に直接渡される追加のパラメータ。

## 例

```jldoctest
julia> model = DeepEquilibriumNetwork(
           Parallel(+, Dense(2, 2; use_bias=false), Dense(2, 2; use_bias=false)),
           VCABM3(); verbose=false);

julia> rng = Xoshiro(0);

julia> ps, st = Lux.setup(rng, model);

julia> size(first(model(ones(Float32, 2, 1), ps, st)))
(2, 1)
```

関連情報: [`SkipDeepEquilibriumNetwork`](@ref)、[`MultiScaleDeepEquilibriumNetwork`](@ref)、[`MultiScaleSkipDeepEquilibriumNetwork`](@ref)。
