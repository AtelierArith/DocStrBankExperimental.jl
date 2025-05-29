```
ckw05(handle, subtyp, degree, begtim, endtim, inst, ref, avflag, segid, sclkdp, packts,
      rate, nints, starts)
```

CKファイルにタイプ5セグメントを書き込みます。

### 引数

  * `handle`: 開いているCKファイルのハンドル
  * `subtyp`: CKタイプ5のサブタイプコード
  * `degree`: 補間多項式の次数
  * `begtim`: セグメントの開始エンコードSCLK
  * `endtim`: セグメントの終了エンコードSCLK
  * `inst`: NAIF機器IDコード
  * `ref`: セグメントの参照フレーム
  * `avflag`: セグメントが角速度を含む場合は真
  * `segid`: セグメント識別子
  * `sclkdp`: エンコードされたSCLK時刻
  * `packts`: パケットの配列
  * `rate`: タイックあたりの秒数での名目SCLKレート
  * `nints`: インターバルの数
  * `starts`: エンコードされたSCLKインターバル開始時刻

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw05_c.html)
