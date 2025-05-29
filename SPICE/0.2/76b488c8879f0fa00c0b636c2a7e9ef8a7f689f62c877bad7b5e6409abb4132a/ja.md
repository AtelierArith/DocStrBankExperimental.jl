```
spkez(targ, et, ref, abcorr, obs)
```

ターゲット天体の状態（位置と速度）を観測天体に対して返します。オプションで光時間（惑星のアバレーション）および恒星のアバレーションの補正が行われます。

### 引数

  * `targ`: ターゲット天体
  * `et`: 観測者のエポック
  * `ref`: 出力状態ベクトルの基準フレーム
  * `abcorr`: アバレーション補正フラグ
  * `obs`: 観測天体

### 出力

  * `starg`: ターゲットの状態
  * `lt`: 観測者とターゲットの間の片道光時間

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkez_c.html)
