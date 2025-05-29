```
prop2b(gm, pvinit, dt)
```

中央質量と時刻 `t_0` における無質量体の状態が与えられた場合、このルーチンは二体力モデルによって予測される状態を時刻 `t_0 + dt` で決定します。

### 引数

  * `gm`: 中央質量の重力。
  * `pvinit`: 状態を伝播させるための初期状態。
  * `dt`: 初期状態から伝播するための時間オフセット。

### 出力

伝播された状態を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/prop2b_c.html)
