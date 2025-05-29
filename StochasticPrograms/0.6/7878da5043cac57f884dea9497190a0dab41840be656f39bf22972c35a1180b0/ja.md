```
@second_stage(def)
```

`stochasticprogram`に第二段階モデル生成レシピを追加するには、次の構文を使用します。

```julia
@second_stage stochasticprogram::StochasticProgram = begin
    @known var1 var2 ...
    ...
end
```

ここで、ブロック内ではJuMP構文を使用して第二段階モデルを定義します。定義中、第二段階モデルは`stochasticprogram`の名前に一致する予約語を通じて参照されます。

## 例

次のように、次の第二段階モデルを定義します。

$$
  minimize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

ここで、$q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$はシナリオ$ξ$に依存し、$x₁, x₂$は第一段階変数です。二つのシナリオが追加され、二つの第二段階モデルが生成されます。

```julia
@second_stage sp = begin
    @known(sp, x₁, x₂)
    @uncertain q₁ q₂ d₁ d₂
    @variable(sp, 0 <= y₁ <= d₁)
    @variable(sp, 0 <= y₂ <= d₂)
    @objective(sp, Min, q₁*y₁ + q₂*y₂)
    @constraint(sp, 6*y₁ + 10*y₂ <= 60*x₁)
    @constraint(sp, 8*y₁ + 5*y₂ <= 80*x₂)
end
```

参照: [`@first_stage`](@ref)
