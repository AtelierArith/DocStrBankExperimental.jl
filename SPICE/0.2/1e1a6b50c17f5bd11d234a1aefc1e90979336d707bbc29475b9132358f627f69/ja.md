```
dskb02(handle, dladsc)
```

DSKタイプ2セグメントから帳簿データを返します。

### 引数

  * `handle`: DSKファイルハンドル
  * `dladsc`: DLA記述子

### 出力

  * `nv`: モデル内の頂点の数
  * `np`: モデル内のプレートの数
  * `nvxtot`: 細かいグリッド内のボクセルの数
  * `vtxbds`: 頂点の境界
  * `voxsiz`: 細かいボクセルの辺の長さ
  * `voxori`: 細かいボクセルグリッドの原点
  * `vgrext`: 細かいボクセルグリッドの範囲
  * `cgscal`: 粗いボクセルグリッドのスケール
  * `vtxnpl`: 頂点-プレート対応リストのサイズ
  * `voxnpt`: ボクセル-プレートポインタリストのサイズ
  * `voxnpl`: ボクセル-プレート対応リストのサイズ

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskb02_c.html)
