```
ckgp(inst, sclkdp, tol, ref)
```

指定された宇宙船時計時間の指向（姿勢）を取得します。

### 引数

  * `inst`: 計算機科学機関（NAIF）のID、機器、宇宙船、または構造
  * `sclkdp`: エンコードされた宇宙船時計時間
  * `tol`: 時間の許容範囲
  * `ref`: 参照フレーム

### 出力

要求された指向が利用できない場合は `nothing` を返します。または

  * `cmat`: C行列の指向データ
  * `clkout`: 出力エンコードされた宇宙船時計時間

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckgp_c.html)
