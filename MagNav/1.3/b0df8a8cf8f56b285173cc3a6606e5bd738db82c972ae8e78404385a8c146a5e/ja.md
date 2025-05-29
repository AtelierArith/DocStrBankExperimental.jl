```
plot_correlation_matrix(xyz::XYZ, ind = trues(xyz.traj.N),
                        features_setup::Vector{Symbol} = [:mag_1_uc,:TL_A_flux_a];
                        terms             = [:permanent],
                        sub_diurnal::Bool = false,
                        sub_igrf::Bool    = false,
                        bpf_mag::Bool     = false,
                        dpi::Int          = 200,
                        Nmax::Int         = 1000,
                        show_plot::Bool   = true,
                        save_plot::Bool   = false,
                        plot_png::String  = "correlation_matrix.png")
```

`2-5`の特徴の相関行列をプロットします。

**引数:**

  * `xyz`:            `XYZ`フライトデータ構造
  * `ind`:            選択されたデータインデックス
  * `features_setup`: 含める特徴のベクトル
  * `terms`:          (オプション) 使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:    (オプション) trueの場合、スカラー磁力計測定から日周変動を引く
  * `sub_igrf`:       (オプション) trueの場合、スカラー磁力計測定からIGRFを引く
  * `bpf_mag`:        (オプション) trueの場合、スカラー磁力計測定をbpfする
  * `dpi`:            (オプション) インチあたりのドット数（画像解像度）
  * `Nmax`:           (オプション) プロットされるデータポイントの最大数
  * `show_plot`:      (オプション) trueの場合、`p1`を表示
  * `save_plot`:      (オプション) trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:       (オプション) 保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: `features`間の相関行列のプロット（`features_setup`から作成）
