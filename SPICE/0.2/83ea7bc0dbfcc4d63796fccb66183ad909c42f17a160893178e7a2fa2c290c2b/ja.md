```
spkezr(targ, et, ref, abcorr, obs)
```

ターゲットボディの状態（位置と速度）を観測ボディに対して返します。オプションで光時間（惑星のアバレーション）と恒星のアバレーションの補正が行われます。

### 引数

  * `targ`: ターゲットボディの名前
  * `et`: 観測者のエポック
  * `ref`: 出力状態ベクトルの基準フレーム
  * `abcorr`: アバレーション補正フラグ
  * `obs`: 観測ボディの名前

### 出力

  * `starg`: ターゲットの状態
  * `lt`: 観測者とターゲットの間の片道光時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkezr_c.html)
