```
lgrind(xvals, yvals, x)
```

指定された座標ペアのセットに対して、指定された横軸値でラグランジュ補間多項式を評価します。多項式とその導関数の値を返します。

### 引数

  * `xvals`: 座標ペアの横軸値
  * `yvals`: 座標ペアの縦軸値
  * `x`: 多項式を補間する点

### 出力

  * `p`: xにおける、xvalsとyvalsで定義された平面上の点にフィットする次数n-1の一意の多項式の値
  * `dp`: 上記の補間多項式のxにおける導関数

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lgrind_c.html)
