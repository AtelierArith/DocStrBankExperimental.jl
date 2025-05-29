```
tipbod(ref, body, et)
```

慣性座標の位置を体赤道およびプライム子午線座標の位置に変換する3×3行列を返します。

### 引数

  * `ref`: 変換元の慣性参照フレームの名前
  * `body`: 体のIDコード
  * `et`: 変換のエポック

### 出力

慣性位置からプライム子午線への変換行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/tipbod_c.html)
