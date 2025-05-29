```
surfpv(stvrtx, stdir, a, b, c)
```

指定された光線、光線速度、および楕円体によって定義された表面交点の状態（位置と速度）を見つけます。

### 引数

  * `stvrtx`: 光線の頂点の状態
  * `stdir`: 光線の方向ベクトルの状態
  * `a`: x軸に沿った楕円体の半軸の長さ
  * `b`: y軸に沿った楕円体の半軸の長さ
  * `c`: z軸に沿った楕円体の半軸の長さ

### 出力

表面交点の状態を返すか、見つからなかった場合は `nothing` を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/surfpv_c.html)
