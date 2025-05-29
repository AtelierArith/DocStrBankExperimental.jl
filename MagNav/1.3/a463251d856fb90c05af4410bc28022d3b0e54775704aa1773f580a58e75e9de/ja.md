```
eval_filt(traj::Traj, ins::INS, filt_res::FILTres)
```

フィルタ結果を抽出します。

**引数:**

  * `traj`:     `Traj` 軌道構造体
  * `ins`:      `INS` 慣性航法システム構造体
  * `filt_res`: `FILTres` フィルタ結果構造体

**戻り値:**

  * `filt_out`: `FILTout` フィルタ抽出出力構造体
