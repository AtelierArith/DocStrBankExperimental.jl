```
spkacs(targ, et, ref, abcorr, obs, starg, lt, dlt)
```

ターゲットボディの状態（位置と速度）を観測者に対して返します。オプションで光時間と星のアバレーションの補正が行われ、慣性参照フレームに対して表現されます。

### 引数

  * `targ`: ターゲットボディ
  * `et`: 観測者のエポック
  * `ref`: 出力状態の慣性参照フレーム
  * `abcorr`: アバレーション補正フラグ
  * `obs`: 観測者

### 出力

  * `starg`: ターゲットの状態
  * `lt`: 観測者とターゲットの間の片道光時間
  * `dlt`: 時間に対する光時間の導関数

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkacs_c.html)
