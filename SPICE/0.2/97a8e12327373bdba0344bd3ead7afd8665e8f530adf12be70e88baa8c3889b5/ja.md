```
pckw02(handle, clssid, frame, first, last, segid, intlen, cdata, btime)
```

PCKバイナリファイルにタイプ2セグメントを書き込むための関数で、ファイルハンドル、フレームクラスID、基準フレーム、セグメントがカバーする時間範囲、およびチェビシェフ多項式係数を指定します。

### 引数

  * `handle`: 書き込み用にオープンされたバイナリPCKファイルのハンドル。
  * `clssid`: 体固定フレームのフレームクラスID。
  * `frame`: 基準参照フレームの名前。
  * `first`: セグメントがカバーする間隔の開始時間。
  * `last`: セグメントがカバーする間隔の終了時間。
  * `segid`: セグメント識別子。
  * `intlen`: 論理レコードがカバーする時間の長さ。
  * `cdata`: チェビシェフ係数の配列。
  * `btime`: 最初の論理レコードの開始時間。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pckw02_c.html)
