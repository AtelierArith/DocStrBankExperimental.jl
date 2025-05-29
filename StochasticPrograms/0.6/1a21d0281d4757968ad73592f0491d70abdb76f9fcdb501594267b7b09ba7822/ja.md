```
@zero(def)
```

@scenarioブロック内で加法的ゼロシナリオを次の構文を使用して定義します：

```julia
@zero begin
    ...
    return zero_scenario
end
```

## 例

以下は、[`@define_scenario`](@ref)で定義された例のシナリオのゼロシナリオを定義します。

```julia
@zero begin
    return ExampleScenario(0.0)
end
```

[`@define_scenario`](@ref)も参照してください。
