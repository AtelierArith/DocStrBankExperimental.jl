```
AbstractVarList
```

[`ReactionMethod`](@ref) `methodfn` に必要な変数は、各々が [`VariableReaction`](@ref) のコレクションを含む Tuple の VarList_xxx <: AbstractVarList によって指定されます。

これらは次に、[`create_accessors`](@ref) メソッドによって、Domain データ配列のビューのコレクションに対応する Tuple に変換され、[`ReactionMethod`](@ref) `methodfn` に渡されます。

注: メタデータを含む供給された変数のコピーを作成して使用するため、VarList を作成する前に変数の属性を設定/変更してください。

# 実装

`AbstractVarList` のサブタイプは以下を実装する必要があります：

  * VariableReactions のコレクションを受け取るコンストラクタ
  * [`create_accessors`](@ref)、サブタイプ特有のコレクションで Domain データ配列のビューを返す。
  * [`get_variables`](@ref)、VariableReactions のコレクション（フラットリストとして）を返す。
