`DecisionTree`は、IF-THEN-ELSEブロックの入れ子構造として機能する象徴的モデルです：

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

ここで、前提は満たすべき式であり、結果はブロックの実行可能なローカルアウトカムです。

実際には、`DecisionTree`は単に`Branch`と`LeafModel`の制約付きサブツリーをラップします：

```
struct DecisionTree{O} <: AbstractModel{O}
    root::M where {M<:AbstractModel}
    info::NamedTuple
end
```

この構造には、追加情報を格納するための`info::NamedTuple`も含まれていることに注意してください。

[`MixedModel`](@ref)や[`DecisionList`](@ref)も参照してください。
