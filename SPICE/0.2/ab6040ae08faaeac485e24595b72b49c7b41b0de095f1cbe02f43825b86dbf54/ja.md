```
ckgpav(inst, sclkdp, tol, ref)
```

指定された宇宙船時計の時間に対する指向（姿勢）と角速度を取得します。

### 引数

  * `inst`: 計測器、宇宙船、または構造のNAIF ID
  * `sclkdp`: エンコードされた宇宙船時計の時間
  * `tol`: 時間の許容範囲
  * `ref`: 参照フレーム

### 出力

要求された指向が利用できない場合は `nothing` を返します。または

  * `cmat`: C行列の指向データ
  * `av`: 角速度ベクトル
  * `clkout`: 出力エンコードされた宇宙船時計の時間

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckgpav_c.html)
