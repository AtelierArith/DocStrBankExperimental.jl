```
instantiate(stochasticmodel::StochasticModel{2},
            scenarios::Vector{<:AbstractScenario};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing;
            defer::Bool = false,
            kw...)
```

二段階の確率プログラムを、二段階の `stochasticmodel` に保存されたモデル定義と、与えられた `scenarios` のコレクションを使用してインスタンス化します。オプションで `optimizer` を指定できます。明示的な `instantiation` が提供されていない場合、構造はオプティマイザによって誘導されます。デフォルトでは構造は `Deterministic` です。
