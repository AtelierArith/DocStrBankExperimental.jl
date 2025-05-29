`MixedModel`は、IF-THEN-ELSEおよびIF-ELSEIF-ELSEブロックの自由なネスト構造として機能する記号モデルです：

```
IF (antecedent_1) THEN
    IF (antecedent_1)     THEN (consequent_1)
    ELSEIF (antecedent_2) THEN (consequent_2)
    ELSE (consequent_1_default) END
ELSE
    IF (antecedent_3) THEN
        (consequent_3)
    ELSE
        (consequent_4)
    END
END
```

ここで、前提はチェックされる式であり、結果はブロックの実行可能なローカル結果です。

Sole.jlでは、このロジックは`Rule`、`Branch`、`DecisionList`、`DecisionTree`などの`AbstractModel`を使用して実装でき、`MixedModel`にラップできます：

```
struct MixedModel{O,FM<:AbstractModel} <: AbstractModel{O}
    root::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

ここで、`FM`はモデルのサブツリーで許可される実行可能モデル（`FM`）を指します。

[`DecisionTree`](@ref)や[`DecisionList`](@ref)も参照してください。
