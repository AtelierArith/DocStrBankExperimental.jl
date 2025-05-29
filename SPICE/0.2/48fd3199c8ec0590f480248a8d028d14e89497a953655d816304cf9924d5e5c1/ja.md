```
spkltc(targ, et, ref, abcorr, stobs)
```

ターゲットボディの状態（位置と速度）を観測者に対して返します。オプションで光時間補正を行い、慣性基準フレームに対して表現されます。

### 引数

  * `targ`: ターゲットボディ
  * `et`: 観測者のエポック
  * `ref`: 出力状態の慣性基準フレーム
  * `abcorr`: 異常補正フラグ
  * `stobs`: SSBに対する観測者の状態

### 出力

  * `starg`: ターゲットの状態
  * `lt`: 観測者とターゲットの間の片道光時間
  * `dlt`: 時間に対する光時間の導関数

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkltc_c.html)
