```
GaussianDispersion(σ::Real, free::NTuple{1, Bool} = (true,)) <: AbstractDispersionModel
```

金属量のガウス（すなわち、正規）分布の分散モデルで、標準偏差 `σ`（0より大きい必要があります）を固定した年齢で使用します。このモデルの相対的な重みは $A_{j,k} = \exp(-((x_k - μ_j)/σ)^2/2).$ で与えられます。`σ` は `free == (true,)` の場合に最適化中にフィットさせることができ、`free == (false,)` の場合は固定されます。

# 例

```jldoctest; setup=:(using StarFormationHistories: nparams, gradient, update_params, transforms, free_params)
julia> GaussianDispersion(0.2) isa GaussianDispersion{Float64}
true

julia> import Test

julia> Test.@test_throws(ArgumentError, GaussianDispersion(-0.2)) isa Test.Pass
true

julia> nparams(GaussianDispersion(0.2)) == 1
true

julia> GaussianDispersion(0.2)(1.0, 1.2) ≈ exp(-0.5)
true

julia> all(values(gradient(GaussianDispersion(0.2), 1.0, 1.2)) .≈
                (3.0326532985631656, -3.0326532985631656))
true

julia> update_params(GaussianDispersion(0.2), 0.3) == GaussianDispersion(0.3)
true

julia> transforms(GaussianDispersion(0.2)) == (1,)
true

julia> free_params(GaussianDispersion(0.2, (false,))) == (false,)
true
```
