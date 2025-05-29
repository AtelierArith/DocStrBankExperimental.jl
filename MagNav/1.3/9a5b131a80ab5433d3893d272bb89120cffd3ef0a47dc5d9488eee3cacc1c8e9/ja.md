```
plot_filt(traj::Traj, ins::INS, filt_out::FILTout;
          dpi::Int        = 200,
          Nmax::Int       = 5000,
          plot_vel::Bool  = false,
          show_plot::Bool = true,
          save_plot::Bool = false)
```

フライトパスと緯度・経度を時間に対してプロットします。

**引数:**

  * `traj`:      `Traj` 軌道構造体
  * `ins`:       `INS` 慣性航法システム構造体
  * `filt_out`:  `FILTout` フィルタ抽出出力構造体
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:      （オプション）プロットされるデータポイントの最大数
  * `plot_vel`:  （オプション）trueの場合、速度をプロット
  * `show_plot`: （オプション）trueの場合、プロットを表示
  * `save_plot`: （オプション）trueの場合、デフォルトのファイル名でプロットを保存

**戻り値:**

  * `p1`: フライトパス
  * `p2`: 緯度と時間
  * `p3`: 経度と時間
  * `p4`: `plot_vel = true` の場合、北向きの速度と時間
  * `p5`: `plot_vel = true` の場合、東向きの速度と時間
