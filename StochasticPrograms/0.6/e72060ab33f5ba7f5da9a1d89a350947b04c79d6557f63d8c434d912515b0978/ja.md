```
expected(scenarios::Vector{<:AbstractScenario})
```

コレクション `scenarios` から期待されるシナリオを [`ExpectedScenario`](@ref) ラッパーで返します。

これは古典的な期待値を通じて定義されます: sum([probability(s)*s for s in scenarios])、および要求されたフィールドがサポートされている場合、@scenario を通じて作成されたシナリオに対して常に定義されています。

そうでない場合、ユーザー定義のシナリオタイプは完全な機能のためにこのメソッドを実装する必要があります。

[`ExpectedScenario`](@ref) も参照してください。
