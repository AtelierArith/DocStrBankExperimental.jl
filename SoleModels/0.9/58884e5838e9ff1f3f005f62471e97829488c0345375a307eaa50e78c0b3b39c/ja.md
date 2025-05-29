```
negconsequent(m::Branch)::AbstractModel
```

ブランチの負の [`consequent`](@ref) を返します。つまり、前件が `false` に評価される場合に適用されるモデルです。

関連項目としては、[`antecedent`](@ref)、[`Branch`](@ref)、[`posconsequent`](@ref) があります。
