```
eval_crlb(traj::Traj, crlb_P::Array)
```

クレメル–ラオ下限（CRLB）結果を抽出します。

**引数:**

  * `traj`:   `Traj` 軌道構造体
  * `crlb_P`: クレメル–ラオ下限非線形共分散行列

**戻り値:**

  * `crlb_out`: `CRLBout` クレメル–ラオ下限抽出出力構造体
