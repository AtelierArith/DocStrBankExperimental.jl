```
AbstractExpressionNode{T} <: AbstractNode
```

式を表すノードのための抽象型。`AbstractNode`に必要なフィールドに加えて、以下のフィールドを持つ必要があります：

  * `constant::Bool`: ノードが定数であるかどうか。
  * `val::T`: ノードの値。`degree==0`で`constant==true`の場合、これは定数の値です。型は`Node`の全体の型によって指定されます（例：`Float64`）。
  * `feature::UInt16`: 特徴ノードの場合に使用する特徴のインデックス。`degree==0`かつ`constant==false`の場合のみ使用されます。`degree == 0 && constant == false`の場合にのみ定義されます。
  * `op::UInt8`: `degree==1`の場合、これは`operators.unaops`内の演算子のインデックスです。`degree==2`の場合、これは`operators.binops`内の演算子のインデックスです。言い換えれば、これは演算子の列挙型であり、特定の`OperatorEnum`オブジェクトに依存します。`degree >= 1`の場合にのみ定義されます。

# インターフェース

インターフェースの実装の完全な説明と正確性を検証するためのテストについては、[`NodeInterface`](@ref DynamicExpressions.InterfacesModule.NodeInterface)を参照してください。

各カスタムノードタイプについて、`CustomNode{_T} where {_T} = new{_T}()`を定義する必要があります。また、`constructorof`および`with_type_parameters`も定義する必要があります。

さらに、特に型に追加のフィールドを追加したい場合は、デフォルトの動作をオーバーライドするために、以下の関数を定義することを選択できます。

  * `leaf_copy`および`branch_copy`
  * `leaf_convert`および`branch_convert`
  * `leaf_equal`および`branch_equal`
  * `leaf_hash`および`branch_hash`
  * `preserve_sharing`
