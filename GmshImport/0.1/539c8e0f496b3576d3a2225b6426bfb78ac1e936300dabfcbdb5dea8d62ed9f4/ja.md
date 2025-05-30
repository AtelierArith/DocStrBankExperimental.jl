```
gmsh_import(filename,
    process_elementtypes = String[],
    add_elementtypes = Dict()
    )
```

GMSH有限要素メッシュファイルをインポートします。

# オプション引数

  * `process_elementtypes`: `https://gitlab.onelab.info/gmsh/gmsh/blob/master/src/common/GmshDefines.h`の定義から派生した要素タイプの名前の配列。要素タイプの名前を導出するには、例えば`#define MSH_QUA_4 3`を例に取ります。`MSH_`を取り除き、アンダースコアをスペースに置き換えます: "QUA 4"。配列`process_elementtypes`が空である場合（デフォルト）、すべての要素タイプが処理されると仮定されます。例: `["LIN 2", ]`は、2つのノードを持つ線要素のみを処理することを要求します。
  * `add_elementtypes`: 追加の要素タイプ定義の辞書。`https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format`を参照してください。辞書は要素タイプの名前（文字列）でインデックス付けされ、値は要素タイプの整数と要素ごとのノード数のタプルです。例: `Dict("TRI 15" => (23, 15),)`を渡すと、15ノードを持つ三角形のタイプが追加されます。現在のデフォルトは`GmshImport.elementtypes_definitions`です。

# 戻り値

  * `nodeblocks`: ノードブロックは、各データを持つ名前付きタプルの配列です:

      * `block` = ブロックID,
      * `entdim` = エンティティ次元,
      * `enttag` = エンティティタグ,
      * `parcoor` = 提供されたパラメトリック座標?,
      * `nnodes` = このエンティティに位置するノードの数,
      * `ntags` = ノードタグの配列,
      * `ncoor` = ノード座標の配列、1行に1ノード。
  * `elementblocks`: エレメントブロックは、各データを持つ名前付きタプルの配列です:

      * `block` = ブロックID,
      * `entdim` = エンティティ次元,
      * `enttag` = エンティティタグ,
      * `elementtypename` = 要素タイプの名前,
      * `elementtype` = 数値要素タイプ（Gmshによって定義されたもの）,
      * `nnodes` = 要素ごとのノード数,
      * `nelements` = このエンティティに位置する要素の数,
      * `etags` = 要素タグの配列,
      * `econn` = 要素接続の配列、1行に1要素。
