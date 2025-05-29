```
tisbod(ref, body, et)
```

慣性座標の状態をボディ-赤道-プライム子午線座標の状態に変換する6×6行列を返します。

### 引数

  * `ref`: 変換元の慣性基準フレームの名前
  * `body`: 天体のIDコード
  * `et`: 変換のエポック

### 出力

慣性状態からプライム子午線への変換行列を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/tisbod_c.html)
