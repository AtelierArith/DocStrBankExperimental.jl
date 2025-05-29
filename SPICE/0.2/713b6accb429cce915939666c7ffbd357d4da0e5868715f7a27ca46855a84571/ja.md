```
spkapo(targ, et, ref, sobs, abcorr)
```

ターゲット天体の位置を観測者に対して返します。光時間および星のアバレーションの補正をオプションで行うことができます。

### 引数

  * `targ`: ターゲット天体
  * `et`: 観測者のエポック
  * `ref`: 観測者の状態の慣性参照フレーム
  * `sobs`: 太陽系重心に対する観測者の状態
  * `abcorr`: アバレーション補正フラグ

### 出力

  * `ptarg`: ターゲットの位置
  * `lt`: 観測者とターゲットの間の片道光時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkapo_c.html)
