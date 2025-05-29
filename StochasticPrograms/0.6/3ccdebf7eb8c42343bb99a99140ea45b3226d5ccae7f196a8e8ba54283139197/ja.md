```
@stage(def)
```

`stochasticprogram`にステージモデル生成レシピを追加するには、次の構文を使用します。

```julia
@stage stage stochasticprogram::StochasticProgram = begin
    @parameters param1 param2 ...
    @decision(stochasticprogram, var) ...
    @uncertain ξ
    ... JuMPdef ...
    ...
end
```

ここで、`stage`はステージ番号であり、ブロック内ではJuMP構文を使用してステージモデルを定義します。定義中、ステージモデルは`stochasticprogram`と同じ変数名を使用して参照されます。

## 例

次のものは、次のように与えられる最初のステージモデルを定義します。

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

および次のように与えられる第二ステージモデル：

$$
  maximize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

ここで、$q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$はシナリオ$ξ$に依存し、$x₁, x₂$は第一ステージ変数です。二つのシナリオが追加され、二つの第二ステージモデルが生成されます。

```jldoctest
ξ₁ = @scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4
ξ₂ = @scenario q₁ = 28.0 q₂ = 32.0 d₁ = 300.0 d₂ = 300.0 probability = 0.6

sp = StochasticProgram([ξ₁, ξ₂])

@stage 1 sp = begin
    @decision(sp, x₁ >= 40)
    @decision(sp, x₂ >= 20)
    @objective(sp, Min, 100*x₁ + 150*x₂)
    @constraint(sp, x₁ + x₂ <= 120)
end

@stage 2 sp = begin
    @uncertain q₁ q₂ d₁ d₂
    @variable(sp, 0 <= y₁ <= d₁)
    @variable(sp, 0 <= y₂ <= d₂)
    @objective(sp, Max, q₁*y₁ + q₂*y₂)
    @constraint(sp, 6*y₁ + 10*y₂ <= 60*x₁)
    @constraint(sp, 8*y₁ + 5*y₂ <= 80*x₂)
end

# output

Stochastic program with:
 * 2 decision variables
 * 2 scenarios of type Scenario
Solver is default solver

```

参照： [`@parameters`](@ref), [`@decision`](@ref), [`@uncertain`](@ref)
