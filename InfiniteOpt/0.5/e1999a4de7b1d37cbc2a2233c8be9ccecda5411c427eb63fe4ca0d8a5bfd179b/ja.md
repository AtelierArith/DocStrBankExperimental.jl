```
JuMP.object_dictionary(model::InfiniteModel)::Dict{Symbol, Any}
```

マクロで定義されたオブジェクト（例えば、パラメータ、変数、または制約）のシンボル名を対応するオブジェクトにマッピングする辞書を返します。オブジェクトはマクロ内の特定のシンボルに登録されます。例えば、`@variable(model, x[1:2, 1:2])`は変数の配列`x`をシンボル`:x`に登録します。
