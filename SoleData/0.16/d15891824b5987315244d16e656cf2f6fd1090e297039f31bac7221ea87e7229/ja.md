```
@scalarformula expr
```

スカラー条件に関する論理式を解析します。例えば `V1 > 10` のようなものです。論理演算子は比較演算子よりも優先されるため、`V1 > 10` のような式はしばしば括弧で囲む必要があります。

# 例

```julia-repl
julia> φ = @scalarformula ((V1 > 10) ∧ (V2 < 0) ∧ (V2 < 0) ∧ (V2 <= 0)) ∨ ((V1 <= 0) ∧ ((V1 <= 3)) ∧ (V2 >= 2))
SyntaxBranch: (V1 > 10 ∧ V2 < 0 ∧ V2 < 0 ∧ V2 ≤ 0) ∨ (V1 ≤ 0 ∧ V1 ≤ 3 ∧ V2 ≥ 2)
```

[`parseformula`](@ref) や [`syntaxstring`](@ref) も参照してください。
