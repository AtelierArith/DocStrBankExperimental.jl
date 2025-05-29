```
surfpt(positn, u, a, b, c)
```

楕円体の表面との視線ベクトルの交点を求めます。

### 引数

  * `positn`: ボディ固定フレームにおける観測者の位置
  * `u`: 観測者からのある方向へのベクトル
  * `a`: x軸に沿った楕円体の半軸の長さ
  * `b`: y軸に沿った楕円体の半軸の長さ
  * `c`: z軸に沿った楕円体の半軸の長さ

### 出力

uが指す楕円体上の点を返すか、見つからなかった場合は`nothing`を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/surfpt_c.html)
