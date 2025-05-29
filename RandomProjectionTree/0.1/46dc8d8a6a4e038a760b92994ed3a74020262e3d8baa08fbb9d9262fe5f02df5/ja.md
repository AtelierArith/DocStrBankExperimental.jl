# RPTree

構造体 RPTree は、ツリー構築中に発生したイベントのリストを保存します。ツリーを成長させるために使用されるパラメータは、フィールド argument に保存されます。

FIELDS

  * treedata : ツリー
  * argument : ツリー成長を説明するパラメータ
  * eventDict : 各ノードで発生したイベント
  * treelock : eventDict を操作するためのロック
