```
uddf(udfunc, x, dx)
```

呼び出し元が指定した関数の一次導関数を三点推定を使用して計算するためのルーチン。

### 引数

  * `udfunc`: スカラー値を計算する呼び出し可能な関数、例: `f(x::Float64) -> Float64`
  * `x`: `udfunc`の独立変数
  * `dx`: 導関数計算のための`x`からの間隔

### 出力

`x`における`udfunc`の近似導関数を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/uddf_c.html)
