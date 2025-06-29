```
p4est_connectivity_read_inp(filename)
```

ABAQUS入力ファイルから`p4est`接続性を作成します。

このユーティリティ関数は、2Dの要素タイプでプレフィックスC2D4、CPS4、S4をサポートし、C3D8タイプの要素をバイリニア四角形およびトリリニア六面体ツリーとして読み取る基本的なABAQUSファイルを読み込みます。

以下に基本的な2Dメッシュを示します。`*Node`セクションは、各頂点の番号とx、y、z成分を示します。`*Element`セクションは、各要素の4つの頂点（3Dでは8つの頂点）を反時計回りの順序で示します。したがって、2Dではノードは次のように示されます：

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

この関数は*filename*からメッシュを読み込み、関連する`p4est`接続性を返します。

### パラメータ

  * `filename`:[in] 接続性を読み込むファイル

### 戻り値

*filename*のメッシュに関連付けられた接続性を割り当てて返すか、エラーが発生した場合はNULLを返します。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_read_inp (const char *filename);
```
