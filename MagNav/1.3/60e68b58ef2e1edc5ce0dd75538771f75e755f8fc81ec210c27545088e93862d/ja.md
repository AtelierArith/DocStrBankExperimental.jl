```
plot_filt_err(traj::Traj, filt_out::FILTout, crlb_out::CRLBout;
              dpi::Int        = 200,
              Nmax::Int       = 5000,
              plot_vel::Bool  = false,
              show_plot::Bool = true,
              save_plot::Bool = false)
```

時間に対する北方向および東方向の誤差をプロットします。

**引数:**

  * `traj`:      `Traj` 軌道構造体
  * `filt_out`:  `FILTout` フィルタ抽出出力構造体
  * `crlb_out`:  `CRLBout` クラメール–ラオ下限抽出出力構造体
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:      （オプション）プロットされるデータポイントの最大数
  * `plot_vel`:  （オプション）trueの場合、速度誤差をプロット
  * `show_plot`: （オプション）trueの場合、プロットを表示
  * `save_plot`: （オプション）trueの場合、デフォルトのファイル名でプロットを保存

**戻り値:**

  * `p1`: 時間に対する北方向の誤差
  * `p2`: 時間に対する東方向の誤差
  * `p3`: `plot_vel = true` の場合、時間に対する北方向の速度誤差
  * `p4`: `plot_vel = true` の場合、時間に対する東方向の速度誤差
