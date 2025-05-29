```
dskxsi(pri, target, nsurf, srflst, et, fixref, vertex, raydir, maxd=1, maxi=1)
```

複数の読み込まれたDSKセグメントによって提供されたデータを使用して、レイ-サーフェスインターセプトを計算します。インターセプトが見つかったサーフェスを定義するデータのソースに関する情報を返します：DSKハンドル、DLAおよびDSK記述子、そしてDSKデータタイプ依存のパラメータ。

### 引数

  * `pri`: データ優先フラグ
  * `target`: 対象天体名
  * `srflst`: サーフェスIDリスト
  * `et`: エポック、J2000 TDBからの経過秒数で表現
  * `fixref`: 対象天体固定参照フレームの名前
  * `vertex`: レイの頂点
  * `raydir`: レイの方向ベクトル
  * `maxd`: DC配列のサイズ（デフォルト: 1）
  * `maxi`: IC配列のサイズ（デフォルト: 1）

### 出力

インターセプトが存在しない場合は`nothing`を返すか、

  * `xpt`: インターセプトポイント
  * `handle`: サーフェスデータに寄与するセグメントのハンドル
  * `dladsc`: セグメントのDLA記述子
  * `dskdsc`: セグメントのDSK記述子
  * `dc`: ソース情報の倍精度コンポーネント
  * `ic`: ソース情報の整数コンポーネント

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskxsi_c.html)
