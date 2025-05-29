```
plot_filt(p1::Plot, traj::Traj, ins::INS, filt_out::FILTout;
          dpi::Int        = 200,
          Nmax::Int       = 5000,
          plot_vel::Bool  = false,
          show_plot::Bool = true,
          save_plot::Bool = false)
```

既存のプロット上に飛行経路をプロットし、時間に対する緯度と経度を表示します。

**引数:**

  * `p1`:        プロット（すなわち、地図）
  * `traj`:      `Traj` 軌道構造体
  * `ins`:       `INS` 慣性航法システム構造体
  * `filt_out`:  `FILTout` フィルタ抽出出力構造体
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:      （オプション）プロットされるデータポイントの最大数
  * `plot_vel`:  （オプション）trueの場合、速度をプロット
  * `show_plot`: （オプション）trueの場合、プロットを表示
  * `save_plot`: （オプション）trueの場合、デフォルトのファイル名でプロットを保存

**戻り値:**

  * `p2`: `p1` に飛行経路を追加したもの
  * `p3`: 時間に対する緯度
  * `p4`: 時間に対する経度
  * `p5`: `plot_vel = true` の場合、時間に対する北向き速度
  * `p6`: `plot_vel = true` の場合、時間に対する東向き速度
