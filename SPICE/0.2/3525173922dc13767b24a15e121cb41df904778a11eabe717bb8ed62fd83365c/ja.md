```
ckw02(handle, begtim, endtim, inst, ref, segid, start, stop, quats, avvs, rates)
```

タイプ2セグメントをCカーネルに書き込みます。

### 引数

  * `handle`: 開いているCKファイルのハンドル
  * `begtim`: セグメントの開始エンコードSCLK
  * `endtim`: セグメントの終了エンコードSCLK
  * `inst`: NAIF機器IDコード
  * `ref`: セグメントの参照フレーム
  * `segid`: セグメント識別子
  * `start`: エンコードされたSCLK間隔の開始時刻
  * `stop`: エンコードされたSCLK間隔の終了時刻
  * `quats`: 機器の指向を表すクォータニオン
  * `avvs`: 角速度ベクトル
  * `rates`: 各間隔のティックあたりの秒数

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw02_c.html)
