```
chbder(cp, x2s, x, nderiv)
```

与えられた多項式のチェビシェフ展開の係数に基づいて、この関数は入力 `x` で評価された多項式とその最初の `nderiv` の導関数の値を返します。

### 引数

  * `cp`: チェビシェフ多項式の係数
  * `x2s`: 多項式の変換パラメータ
  * `x`: 多項式を評価するための値
  * `nderiv`: 計算する導関数の数

### 出力

多項式の導関数を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/chbder_c.html)
