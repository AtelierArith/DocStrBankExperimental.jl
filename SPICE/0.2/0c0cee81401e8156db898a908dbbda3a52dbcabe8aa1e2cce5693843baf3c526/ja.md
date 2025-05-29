```
ckw03(handle, begtim, endtim, inst, ref, segid, sclkdp, quats, starts, avvs=[zeros(3)])
```

Cカーネルにタイプ3セグメントを追加します。

### 引数

  * `handle`: 開いているCKファイルのハンドル
  * `begtim`: セグメントの開始エンコードSCLK
  * `endtim`: セグメントの終了エンコードSCLK
  * `inst`: NAIF機器IDコード
  * `ref`: セグメントの参照フレーム
  * `segid`: セグメント識別子
  * `sclkdp`: エンコードされたSCLK時間
  * `quats`: 機器の指向を表すクォータニオン
  * `starts`: エンコードされたSCLK間隔の開始時間
  * `avvs`: 角速度ベクトル（オプション）

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw03_c.html)
