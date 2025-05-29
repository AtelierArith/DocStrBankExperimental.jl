```
spkpos(targ, et, ref, abcorr, obs)
```

観測体に対するターゲット天体の位置を返します。光時間（惑星のアベレーション）および恒星のアベレーションの補正をオプションで行うことができます。

### 引数

  * `targ`: ターゲット天体の名前
  * `et`: 観測者のエポック
  * `ref`: 出力位置ベクトルの基準フレーム
  * `abcorr`: アベレーション補正フラグ
  * `obs`: 観測体の名前

### 出力

  * `ptarg`: ターゲットの位置
  * `lt`: 観測者とターゲットの間の片道光時間

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpos_c.html)
