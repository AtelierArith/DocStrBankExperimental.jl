```
Formula(formula[, composition][, charge], name=nothing)
```

化学的な `formula` を電気的な `charge` とオプションの `name` で表現します。`composition` は指定された `formula` から自動的に決定されます。化合物は括弧でグループ化でき、協調分子は * で注釈を付けることができます。元素は `Symbol` で表されます。`charge` が指定されていない場合、`formula` 内の上付き文字の電荷から決定されます。デフォルトは 0 です。

# 例

```julia-repl
julia> Formula("H2O", "water")
Formula("H2O", Dict{Symbol, Int32}(:H => 2, :O => 1), 0, "water")
julia> Formula("SO4", -2)
Formula("SO4", Dict{Symbol, Int32}(:S => 1, :O => 4), -2, nothing)
julia> Formula("Fe(CN)6*5H2O")
Formula("Fe(CN)6*5H2O", Dict{Symbol, Int32}(:N => 6, :Fe => 1, :H => 10, :O => 5, :C => 6), 0, nothing)
julia> Formula("SO₄²⁻")
Formula("SO₄²⁻", Dict{Symbol, Int32}(:S => 1, :O => 4), -2, nothing)
```
