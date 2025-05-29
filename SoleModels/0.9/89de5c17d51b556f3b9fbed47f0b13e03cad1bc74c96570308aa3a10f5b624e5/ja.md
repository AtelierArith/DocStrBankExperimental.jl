```
struct MixedModel{O,FM<:AbstractModel} <: AbstractModel{O}
    root::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

[`MixedModel`](@ref) は、[`Rule`](@ref) や [`Branch`](@ref) や [`DecisionList`](@ref) や [`DecisionTree`](@ref) などの複数の [`AbstractModel`](@ref) をラップするものです。

言い換えれば、[`MixedModel`](@ref) は、IF-THEN-ELSE および IF-ELSEIF-ELSE ブロックの自由なネスト構造として機能する象徴的なモデルです：

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

ここで、[`antecedent`](@ref) はチェックされる式であり、[`consequent`](@ref) はブロックの実行可能なローカル結果です。

!!! note
    `FM` はモデルのサブツリーで許可される実行可能モデル（`FM`）を指します。


また、[`AbstractModel`](@ref)、[`Branch`](@ref)、[`DecisionList`](@ref)、[`DecisionTree`](@ref)、[`Rule`](@ref) も参照してください。
