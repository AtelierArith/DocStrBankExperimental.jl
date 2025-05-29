```
NLPExpr <: JuMP.AbstractJuMPScalar
```

スカラー非線形式を格納するための `DataType` です。式は、各ノードが [`NodeData`](@ref) を含む式ツリーを介して代数的に格納され、以下のいずれかを格納できます。

  * 登録された関数名（`Symbol` として格納）
  * 定数
  * 変数
  * アフィン式
  * 二次式

具体的には、式ツリーを表現するために左子右兄弟ツリー（`LeftChildRightSiblingTrees.jl` から）を使用します。

**フィールド**

  * `tree_root::LeftChildRightSiblingTrees.Node{NodeData}`: 式ツリーのルートノード。
