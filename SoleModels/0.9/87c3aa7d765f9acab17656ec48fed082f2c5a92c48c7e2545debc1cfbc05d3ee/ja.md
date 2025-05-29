```
apply(m::AbstractModel, i::AbstractInterpretation; kwargs...)::outputtype(m)

apply(
    m::AbstractModel,
    d::AbstractInterpretationSet;
    kwargs...
)::AbstractVector{<:outputtype(m)}
```

モデル `m` の論理解釈 `i` に対する出力予測を返します。データセット `d` の `i_instance` に対して、またはデータセット `d` のすべてのインスタンスに対して予測を行います。モデルが*不完全*な場合（例：モデルが `Rule` の場合）、予測は `nothing` になる可能性があることに注意してください。

# キーワード引数

  * `check_args::Tuple = ()`;
  * `check_kwargs::NamedTuple = (;)`;
  * `functional_args::Tuple = ()`;
  * `functional_kwargs::NamedTuple = (;)`;
  * 追加のキーワード引数はモデルのサブツリーの葉に渡されます

`check_args` と `check_kwargs` は、計算時のチェックの動作に影響を与えることがあります（[`SoleLogics.check`](@ref)を参照）。

`functional_args` と `functional_kwargs` は、対応する関数が AbstractInterpretation に適用されるときの FunctionModel の動作に影響を与えることがあります（[`FunctionModel`](@ref)、[`SoleLogics.AbstractInterpretation`](@ref)を参照）。

関数のモデル状態を変更するバージョンである [`apply!`] が存在します。この関数は出力を生成する際に、モデルの一部の統計的パフォーマンスを検査するのに役立つ情報キー `:supporting_labels` と `:supporting_predictions` に影響を与えます。

また、`SoleLogics.AbstractInterpretation`、`SoleLogics.AbstractInterpretationSet`、[`AbstractModel`](@ref)、[`iscomplete`](@ref)、[`readmetrics`](@ref) も参照してください。
