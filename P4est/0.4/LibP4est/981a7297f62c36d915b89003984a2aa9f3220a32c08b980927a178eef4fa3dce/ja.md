```
p4est_connectivity_read_inp_stream(stream, num_vertices, num_trees, vertices, tree_to_vertex)
```

ABAQUS入力ファイルをファイルストリームから読み込みます。

このユーティリティ関数は、2Dの要素タイプであるC2D4、CPS4、S4のプレフィックスを持つ基本的なABAQUSファイルを読み込み、C3D8タイプを持つものをそれぞれバイリニア四辺形およびトリリニア六面体ツリーとして読み込みます。

基本的な2Dメッシュは以下の通りです。`*Node`セクションは、各頂点の頂点番号とx、y、z成分を示します。`*Element`セクションは、各要素の4つの頂点（3Dでは8つの頂点）を反時計回りの順序で示します。したがって、2Dではノードは次のように示されます：

4 3 +–––––––––-+ | | | | | | | | | | | | +–––––––––-+ 1 2

3Dでは次のように示されます：

8 7 +––––––––––-+ |\ |\ | \ | \ | \ | \ | \ | \ | 5+––––––––––-+6 | | | | +––|––––––––+ | 4\ | 3 \ | \ | \ | \ | \ | \| \| +––––––––––-+ 1 2

```c++
 *Heading
  box.inp
 *Node
 1,  -5, -5, 0
 2,   5, -5, 0
 3,   5,  5, 0
 4,  -5,  5, 0
 5,   0, -5, 0
 6,   5,  0, 0
 7,   0,  5, 0
 8,  -5,  0, 0
 9,   1, -1, 0
 10,  0,  0, 0
 11, -2,  1, 0
 *Element, type=CPS4, ELSET=Surface1
 1,  1, 10, 11, 8
 2,  3, 10, 9,  6
 3,  9, 10, 1,  5
 4,  7,  4, 8, 11
 5, 11, 10, 3,  7
 6,  2,  6, 9,  5
```

このコードは2つの方法で呼び出すことができます。最初は、`vertex`==NULLおよび`tree_to_vertex`==NULLのときに、*stream*内のメッシュから生成される接続性の木と頂点の数をカウントするために使用されます。2番目は、`vertices`!=NULLおよび`tree_to_vertex`!=NULLのときに、`vertices`と`tree_to_vertex`を埋めます。この場合、`num_vertices`と`num_trees`は、`vertices`と`tree_to_vertex`に割り当てられた最大エントリ数に設定する必要があります。

### パラメータ

  * `stream`:[in,out] 接続性を読み込むためのファイルストリーム
  * `num_vertices`:[in,out] 接続性の頂点数
  * `num_trees`:[in,out] 接続性の木の数
  * `vertices`:[out] 接続性の`vertices`のリスト
  * `tree_to_vertex`:[out] 接続性の`tree_to_vertex`マップ

### 戻り値

成功した場合は0、そうでない場合は非ゼロを返します。

### プロトタイプ

```c
int p4est_connectivity_read_inp_stream (FILE * stream, p4est_topidx_t * num_vertices, p4est_topidx_t * num_trees, double *vertices, p4est_topidx_t * tree_to_vertex);
```
