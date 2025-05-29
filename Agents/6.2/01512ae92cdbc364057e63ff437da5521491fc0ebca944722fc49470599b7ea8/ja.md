```
@multiagent YourAgentType(AgentTypesToMerge...) [<: OptionalSupertype]
```

複数のエージェント「サブタイプ」を定義します。これは、ユニークなタイプ `YourAgentType` のバリアントを意味します。つまり、すべての「サブタイプ」は、全体的なタイプに含まれています。そのため、`typeof` に基づいてそれらを区別することはできず、代わりに `variantof` 関数を使用する必要があります。すべてのバリアントタイプを取得する便利な方法として `allvariants` 関数があります。

なぜしばしば `@multiagent` を使用する方が複数のエージェントタイプを作成するよりも良いのかについては、[チュートリアル](@ref)や[`Union` タイプとのパフォーマンス比較](@ref multi_vs_union)を参照してください。

`@multiagent` は LightSumTypes.jl に基づいています。

## 例

次の定義があるとしましょう：

```
@agent struct Wolf
    energy::Float64 = 0.5
    ground_speed::Float64
    const fur_color::Symbol
end
@agent struct Hawk{T}
    energy::Float64 = 0.1
    ground_speed::Float64
    flight_speed::T
end

@multiagent Animal(Wolf, Hawk{Float64})
```

次のようにして `Wolf` と `Hawk` エージェントを作成できます。

```
hawk_1 = (Animal ∘ Hawk)(1, (1, 1), 1.0, 2.0, 3)
hawk_2 = (Animal ∘ Hawk)(; id = 2, pos = (1, 2), ground_speed = 2.3, flight_speed = 2)
wolf_1 = (Animal ∘ Wolf)(3, (2, 2), 2.0, 3.0, :black)
wolf_2 = (Animal ∘ Wolf)(; id = 4, pos = (2, 1), ground_speed = 2.0, fur_color = :white)
```

エージェントのバリアントを取得する方法は、`variantof` 関数を通じて行います。例えば：

```
variantof(hawk_1) # Hawk
variantof(wolf_2) # Wolf
```

また、バリアント `function` を使用して、内包されたバリアントインスタンスにアクセスすることもできます。

```
variant(hawk_1) # Hawk(1, (1, 1), 1.0, 2.0, 3.0)
variant(wolf_1) # Wolf(3, (2, 2), 2.0, 3.0, :black)
```

このマクロをモデルで使用する方法については、[ウサギ-キツネ-タカの例](@ref rabbit_fox_hawk)を参照してください。
