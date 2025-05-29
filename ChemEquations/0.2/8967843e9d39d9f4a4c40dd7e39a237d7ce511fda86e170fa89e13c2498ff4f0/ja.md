```julia
string(compound::ChemEquations.Compound) -> String

```

化合物を表す文字列を作成します。

すべての元素は一度だけ表示され（例：`"H2O"`、`"HOH"`ではなく）、元々与えられた順序で表示されます（例：`"MgO2H2"`は`cc"Mg(OH)2"`から）、係数が1のものは表示されません（例：`"H"`、`"H1"`ではなく）。

# 例

```jldoctest
julia> string(cc"CuSO4 * 5 H2O")
"CuSO9H10"
```
