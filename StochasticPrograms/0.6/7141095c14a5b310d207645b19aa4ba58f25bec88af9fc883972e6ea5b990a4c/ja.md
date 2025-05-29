```
@uncertain(def)
```

`@stage`ブロック内で、各不確実変数を次の構文を使用して注釈します。

```julia
@uncertain var1, var2, ...
```

またはJuMPのコンテナ構文を使用して

```julia
@uncertain ξ[i=..., j=..., ...]
```

これは[`Scenario`]型が使用されることを前提としています。対応するシナリオデータは、[`@scenario`](@ref)を使用して便利に作成されます。

また、ユーザー定義のシナリオは、型に注釈を付けることで指定できます。さらに、`@stochastic*model`ブロック内では、`@uncertain`注釈中にユーザー定義のシナリオを作成することができ、[`@define*scenario`](@ref)構文を使用します。

## 例

以下は、`@stage`ブロック内でランダムベクトル$[q₁(ξ) q₂(ξ) d₁(ξ) d₂(ξ)]$を宣言し、確率$0.4$および値$[24.0 28.0 500.0 100.0]$の対応するシナリオインスタンスを作成する同等の方法です。

```julia
@uncertain q₁ q₂ d₁ d₂
ξ₁ = @scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4

@uncertain ξ[i in 1:4]
ξ₁ = @scenario ξ[i in 1:4] = [24.0, 28.0, 500.0, 100.0] probability = 0.4

@define_scenario SimpleScenario = begin
    q₁::Float64
    q₂::Float64
    d₁::Float64
    d₂::Float64
end
@uncertain ξ::SimpleScenario
ξ₁ = SimpleScenario(24.0, 28.0, 500.0, 100.0, probability = 0.4)

@stochastic_model begin
    ...
    @uncertain ξ::SimpleScenario = begin
        q₁::Float64
        q₂::Float64
        d₁::Float64
        d₂::Float64
    end
    ...
end
ξ₁ = SimpleScenario(24.0, 28.0, 500.0, 100.0 probability = 0.4)
```

[`@scenario`](@ref)、[`@define_scenario`](@ref)、[`@parameters`](@ref)、[`@decision`](@ref)、[`@stage`](@ref)も参照してください。
