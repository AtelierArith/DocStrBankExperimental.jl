```
@define_scenario(def)
```

StochasticProgramsと互換性のあるシナリオタイプを次の構文を使用して定義します。

```julia
@define_scenario name = begin
    ...structdef...

    [@zero begin
        ...
        return zero(scenario)
    end]

    [@expectation begin
        ...
        return expected(scenarios)
     end]
end
```

生成されたタイプは`name`を通じて参照され、デフォルトコンストラクタが常に生成されます。このコンストラクタは、シナリオが発生する確率を設定するためにキーワード`probability`を受け入れます。それ以外の場合、内部変数や特化したコンストラクタは、他のJulia構造体と同様に@define_scenarioブロック内で定義されます。

可能であれば、定義されたタイプのために`zero`メソッドと`expected`メソッドが生成されます。そうでない場合、またはデフォルトの実装が望ましくない場合は、これらは[`@zero`](@ref)および[`@expectation`](@ref)を通じてユーザーが提供できます。

定義されたシナリオタイプは、すべてのJuliaプロセスで利用可能です。

## 例

以下は、単一の値を持つシンプルなシナリオ$ξ$を定義します。

```jldoctest
@define_scenario ExampleScenario = begin
    ξ::Float64
end

ExampleScenario(1.0, probability = 0.5)

# 出力

ExampleScenario with probability 0.5
  ξ: 1.0

```

参照: [`@zero`](@ref), [`@expectation`](@ref), [`@sampler`](@ref)
