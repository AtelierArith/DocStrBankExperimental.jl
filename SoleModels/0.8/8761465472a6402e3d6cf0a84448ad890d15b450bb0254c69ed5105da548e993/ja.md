```
apply(m, i; kwargs...)::outputtype(m)
apply(m, d; kwargs...)::AbstractVector{<:outputtype(m)}
apply(m, d, i_instance; kwargs...)::outputtype(m)
```

モデル `m` の出力予測を、論理解釈 `i` に対して、データセット `d` の `i_instance` に対して、またはデータセット `d` のすべてのインスタンスに対して返します。モデルが *open* である場合（例えば、モデルが `Rule` の場合）、予測は `nothing` になる可能性があることに注意してください。

# キーワード引数

  * `check_args::Tuple = ()`;
  * `check_kwargs::NamedTuple = (;)`;
  * `functional_args::Tuple = ()`;
  * `functional_kwargs::NamedTuple = (;)`;
  * 追加のキーワード引数はモデルのサブツリーの葉に渡されます

`check_args` と `check_kwargs` は、計算時のチェックの動作に影響を与える可能性があります（[`SoleLogics.check](@ref)）を参照）。

`functional_args` と `functional_kwargs` は、対応する関数が AbstractInterpretation に適用されるときの FunctionModel の動作に影響を与える可能性があります（[`FunctionModel`](@ref)、[`SoleLogics.AbstractInterpretation](@ref)）を参照）。

関数のモデル状態を変更するバージョンである [`apply!`] は存在します。この関数は出力を生成する際に、モデルの一部の統計的パフォーマンスを検査するのに役立つ情報キー `:supporting_labels` と `:supporting_predictions` に影響を与えます。

また、[`isopen`](@ref)、[`readmetrics`](@ref)、[`AbstractModel`](@ref)、[`SoleLogics.AbstractInterpretation`](@ref)、[`SoleLogics.AbstractInterpretationSet`](@ref) も参照してください。
