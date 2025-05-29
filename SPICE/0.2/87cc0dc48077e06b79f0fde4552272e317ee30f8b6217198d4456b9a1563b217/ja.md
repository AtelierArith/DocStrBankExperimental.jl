```
dskmi2(vrtces, plates, finscl, corscl, worksz, voxpsz, voxlsz, makvtl, spaisz)
```

DSKタイプ2セグメントの空間インデックスを作成します。

### 引数

  * `vrtces`: 頂点
  * `plates`: プレート
  * `finscl`: 細かいボクセルスケール
  * `corscl`: 粗いボクセルスケール
  * `worksz`: ワークスペースサイズ
  * `voxpsz`: ボクセル-プレートポインタ配列サイズ
  * `voxlsz`: ボクセル-プレートリスト配列サイズ
  * `makvtl`: 頂点-プレートリストフラグ
  * `spxisz`: 空間インデックス整数コンポーネントサイズ

### 出力

  * `spaixd`: 空間インデックスの倍精度コンポーネント。
  * `spaixi`: 空間インデックスの整数コンポーネント。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskmi2_c.html)
