```
eval_results(traj::Traj, ins::INS, filt_res::FILTres, crlb_P::Array)
```

CRLB、INS、およびフィルタ結果を抽出します。

**引数:**

  * `traj`:     `Traj` 軌道構造体
  * `ins`:      `INS` 慣性航法システム構造体
  * `filt_res`: `FILTres` フィルタ結果構造体
  * `crlb_P`:   クラメル–ラオ下限非線形共分散行列

**戻り値:**

  * `crlb_out`: `CRLBout` クラメル–ラオ下限抽出出力構造体
  * `ins_out`:  `INSout`  慣性航法システム抽出出力構造体
  * `filt_out`: `FILTout` フィルタ抽出出力構造体
