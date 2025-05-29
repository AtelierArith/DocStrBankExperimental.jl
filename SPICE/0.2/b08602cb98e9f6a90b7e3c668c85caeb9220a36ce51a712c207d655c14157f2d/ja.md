```
ckcov(ck, idcode, needav, level, tol, timsys)
```

指定されたCKファイル内の指定されたオブジェクトのカバレッジウィンドウを見つけます。

### 引数

  * `ck`: CKファイルの名前
  * `idcode`: オブジェクトのIDコード
  * `needav`: 角速度が必要かどうかを示すフラグ
  * `level`: カバレッジレベル:  "SEGMENT" または "INTERVAL"
  * `tol`: タイムティックの許容誤差
  * `timsys`: カバレッジを表すために使用される時間システム

### 出力

`idcode`のカバレッジを示すウィンドウ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckcov_c.html)
