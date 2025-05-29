```
Cellrule <: Rule
```

単一のセルの状態を読み取り、使用するだけの `Rule` であり、その戻り値は同じセルに書き戻されます。

この制限は、ルール間で書き込みが発生しないように [`Chain`](@ref) でルールをラップするなど、パフォーマンス最適化に役立ちます。

`CellRule` は次のように定義されます：

```jldoctest yourcellrule
using DynamicGrids
struct MyCellRule{R,W} <: CellRule{R,W} end
# output
```

そして、次のように適用されます：

```jldoctest yourcellrule
function applyrule(data, rule::MyCellRule, state, I)
    state * 2
end
# output
applyrule (generic function with 1 method)
```

`applyrule` でインデックス `I` が提供されるため、これを使用して [`Aux`](@ref) データを参照できます。
