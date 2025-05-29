# TreeNode{T,U}

## フィールド

Treenodeは以下で構成されています。

  * 距離が存在する必要がある汎用構造体Tのデータの配列。
  * depth : 木の深さ、ルートノードは深さ0にあります。
  * rankInParent : ノードがparent.childrenフィールド内のどこにあるか。
  * おそらく親ノード。
  * 子ノードの配列。
  * Treeを使用するアプリケーションによる可能性のある使用のためのタイプUのいくつかのプライベートデータ。

## コンストラクタ

1. `function TreeNode{T,U}(parentArg::TreeNode{T,U}, dataArg::T)`。       親ノードが指定され、データがある完全なコンストラクタ。
2. `function TreeNode{T,U}(dataArg::T, privatedata::U)`。      親なしのルートノード用のコンストラクタ。
3. `function TreeNode{T, U}(dataArg::T)`
