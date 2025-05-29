```
@observables name symbol_funcs::AbstractDict
@observables name symbols funcs
```

与えられた `name` を持つ [`AbstractObservables`](@ref) サブタイプを生成し、そのフィールドは与えられた `symbols` イテラブルによって示されます。 [`measure!`](@ref) メソッドも、提供された [`funcs`] イテラブルを使用して実装されます。

あるいは、シンボル-関数ペアの `Dict` を単一の引数として提供することもできます。

!!! note
    `length(symbols) == length(funcs)` は構造上の条件です。

