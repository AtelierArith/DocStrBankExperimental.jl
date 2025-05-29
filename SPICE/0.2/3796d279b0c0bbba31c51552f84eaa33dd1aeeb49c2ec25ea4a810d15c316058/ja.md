```
spkgeo(targ, et, ref, obs)
```

ターゲット天体の幾何学的状態（位置と速度）を観測天体に対して計算します。

### 引数

  * `targ`: ターゲット天体。
  * `et`: ターゲットエポック。
  * `ref`: ターゲット参照フレーム。
  * `obs`: 観測天体。

### 出力

  * `state`: ターゲットの状態。
  * `lt`: 光時間。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkgeo_c.html)
