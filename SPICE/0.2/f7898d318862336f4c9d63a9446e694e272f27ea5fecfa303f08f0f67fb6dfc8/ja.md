```
inedpl(a, b, c, plane)
```

三軸楕円体と平面の交点を求めます。

### 引数

  * `a`: x軸上にある楕円体の半軸の長さ
  * `b`: y軸上にある楕円体の半軸の長さ
  * `c`: z軸上にある楕円体の半軸の長さ
  * `plane`: 楕円体と交差する平面

### 出力

  * `ellipse`: 交差する楕円

楕円が見つからない場合は `nothing` を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/inedpl_c.html)
