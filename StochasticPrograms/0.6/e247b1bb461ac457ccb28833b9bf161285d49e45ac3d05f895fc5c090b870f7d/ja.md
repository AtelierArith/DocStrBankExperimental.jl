```
instantiate(stochasticmodel::StochasticModel,
            scenarios::Vector{<:AbstractScenario};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            defer::Bool = false,
            kw...)
```

`stochasticmodel`に格納されたモデル定義と、与えられた`scenarios`のコレクションを使用して確率プログラムをインスタンス化します。オプションで`optimizer`を指定できます。明示的な`instantiation`が提供されていない場合、構造はオプティマイザによって誘導されます。構造はデフォルトで`Deterministic`です。
