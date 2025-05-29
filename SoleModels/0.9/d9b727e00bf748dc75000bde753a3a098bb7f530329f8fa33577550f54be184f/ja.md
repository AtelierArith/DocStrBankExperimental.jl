```
struct DecisionTree{O} <: AbstractModel{O}
    root::M where {M<:Union{LeafModel{O},Branch{O}}}
    info::NamedTuple
end
```

[`DecisionTree`](@ref) は、[`Branch`](@ref) と [`LeafModel`](@ref) の制約されたサブツリーをラップします。

言い換えれば、[`DecisionTree`](@ref) は、IF-THEN-ELSE ブロックのネストされた構造として機能する象徴的なモデルです：

```
IF (antecedent_1) THEN
    IF (antecedent_2) THEN
        (consequent_1)
    ELSE
        (consequent_2)
    END
ELSE
    IF (antecedent_3) THEN
        (consequent_3)
    ELSE
        (consequent_4)
    END
END
```

ここで、[`antecedent`](@ref) は条件式であり、[`consequent`](@ref) はブロックの実行可能なローカル結果です。

!!!note     この構造には、追加情報を格納するための `info::NamedTuple` も含まれていることに注意してください。

他にも [`Branch`](@ref)、[`DecisionList`](@ref)、[`DecisionForest`](@ref)、[`LeafModel`](@ref)、[`MixedModel`](@ref) を参照してください。
