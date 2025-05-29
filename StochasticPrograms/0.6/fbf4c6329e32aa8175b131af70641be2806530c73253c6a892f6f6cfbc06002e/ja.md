```
@expectation(def)
```

[`@define_scenario`](@ref) ブロック内で期待されるシナリオを形成する方法を定義します。シナリオコレクションは予約語 `scenarios` を通じてアクセスされます。

```julia
@zero begin
    ...
    return zero_scenario
end
```

## 例

以下は、[`@scenario`](@ref) で定義された例のシナリオに対する期待を定義します。

```julia
@expectation begin
    return ExampleScenario(sum([probability(s)*s.ξ for s in scenarios]))
end
```

[`@define_scenario`](@ref) も参照してください。
