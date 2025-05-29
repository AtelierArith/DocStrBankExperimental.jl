```
probability(scenario::AbstractScenario)
```

`situation`が発生する確率を返します。

これは、@scenarioを通じて作成されたシナリオに対して常に定義されています。他のユーザー定義のシナリオタイプは、適切な確率を生成するためにこのメソッドを実装する必要があります。デフォルトの動作は、`scenario`が[`Probability`](@ref)型の`probability`フィールドを持つと仮定することです。

関連情報: [`Probability`](@ref)
