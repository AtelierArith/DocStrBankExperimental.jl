```
plot_filt!(p1::Plot, traj::Traj, ins::INS, filt_out::FILTout;
           dpi::Int        = 200,
           Nmax::Int       = 5000,
           show_plot::Bool = true,
           save_plot::Bool = false)
```

既存のプロットにフライトパスをプロットします。

**引数:**

  * `p1`:        プロット（地図）
  * `traj`:      `Traj` 軌道構造体
  * `ins`:       `INS` 慣性航法システム構造体
  * `filt_out`:  `FILTout` フィルタ抽出出力構造体
  * `dpi`:       （オプション）ドット毎インチ（画像解像度）
  * `Nmax`:      （オプション）プロットされるデータポイントの最大数
  * `show_plot`: （オプション）trueの場合、プロットを表示
  * `save_plot`: （オプション）trueの場合、デフォルトのファイル名でプロットを保存

**戻り値:**

  * `nothing`: フライトパスが `p1` にプロットされます
