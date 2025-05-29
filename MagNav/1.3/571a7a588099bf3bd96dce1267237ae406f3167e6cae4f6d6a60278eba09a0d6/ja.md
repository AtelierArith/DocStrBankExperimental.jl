```
plot_mag_c(xyz::XYZ,xyz_comp::XYZ;
           ind                      = trues(xyz.traj.N),
           ind_comp                 = trues(xyz_comp.traj.N),
           detrend_data::Bool       = true,
           λ                        = 0.025,
           terms                    = [:permanent,:induced,:eddy],
           pass1                    = 0.1,
           pass2                    = 0.9,
           fs                       = 10.0,
           use_mags::Vector{Symbol} = [:all_mags],
           use_vec::Symbol          = :flux_a,
           plot_diff::Bool          = false,
           plot_mag_1_uc::Bool      = true,
           plot_mag_1_c::Bool       = true,
           ylim                     = (),
           dpi::Int                 = 200,
           show_plot::Bool          = true,
           save_plot::Bool          = false,
           plot_png::String         = "scalar_mags_comp.png")
```

与えられたフライトテストから補正された磁力計データをプロットします。Mag 1（すなわち、`:mag_1_uc` と `:mag_1_c`）が最良の磁力計（すなわち、スティンガー）であると仮定します。

**引数:**

  * `xyz`:           `XYZ` フライトデータ構造
  * `xyz_comp`:      補正に使用する `XYZ` フライトデータ構造
  * `ind`:           （オプション）選択されたデータインデックス
  * `ind_comp`:      （オプション）補正に使用する選択されたデータインデックス
  * `detrend_data`:  （オプション）trueの場合、プロットデータのトレンドを除去
  * `λ`:             （オプション）リッジパラメータ
  * `terms`:         （オプション）使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:         （オプション）フィルタの第一パスバンド周波数 [Hz]
  * `pass2`:         （オプション）フィルタの第二パスバンド周波数 [Hz]
  * `fs`:            （オプション）フィルタのサンプリング周波数 [Hz]
  * `use_mags`:      （オプション）プロットするスカラーまたはベクトル（フラックスゲート）磁力計 {`:all_mags`, または `:mag_1_uc` など}

      * `:all_mags` = 補正されていないすべてのスカラー磁力計フィールド（例：`:mag_1_uc` など）
  * `use_vec`:       （オプション）トレス・ローソン `A` 行列に使用するベクトル磁力計（フラックスゲート） {`:flux_a` など}
  * `plot_diff`:     （オプション）trueの場合、`提供された` 補正データと補正された磁力計の間の差をプロット
  * `plot_mag_1_uc`: （オプション）trueの場合、mag*1*uc（補正されていない mag_1）をプロット
  * `plot_mag_1_c`:  （オプション）trueの場合、mag*1*c（補正された mag_1）をプロット
  * `ylim`:          （オプション）長さ`2`のプロット `y` 制限（`ymin`,`ymax`） [nT]
  * `dpi`:           （オプション）インチあたりのドット数（画像解像度）
  * `show_plot`:     （オプション）trueの場合、`p1`を表示
  * `save_plot`:     （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:      （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: 補正された磁力計データのプロット
