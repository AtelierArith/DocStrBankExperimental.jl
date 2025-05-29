```
instantiate(stochasticmodel::StochasticModel{2};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            scenario_type::Type{S} = Scenario,
            defer::Bool = false,
            kw...) where S <: AbstractScenario
```

2段階の確率プログラムを、シナリオタイプ `S` に対して `stochasticmodel` に保存されたモデル定義を使用して遅延インスタンス化します。オプションで `optimizer` を指定できます。明示的な `instantiation` が提供されていない場合、構造はオプティマイザによって誘導されます。構造はデフォルトで `Deterministic` です。
