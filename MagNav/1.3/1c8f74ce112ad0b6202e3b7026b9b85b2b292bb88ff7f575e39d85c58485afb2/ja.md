```
plot_mag(xyz::XYZ;
         ind                       = trues(xyz.traj.N),
         detrend_data::Bool        = false,
         use_mags::Vector{Symbol}  = [:all_mags],
         vec_terms::Vector{Symbol} = [:all],
         ylim::Tuple               = (),
         dpi::Int                  = 200,
         show_plot::Bool           = true,
         save_plot::Bool           = false,
         plot_png::String          = "scalar_mags.png")
```

与えられたフライトテストからスカラーまたはベクトル（フラックスゲート）磁力計データをプロットします。

**引数:**

  * `xyz`:          `XYZ` フライトデータ構造体
  * `ind`:          （オプション）選択されたデータインデックス
  * `detrend_data`: （オプション）trueの場合、プロットデータのトレンドを除去
  * `use_mags`:     （オプション）プロットするスカラーまたはベクトル（フラックスゲート）磁力計 {`:all_mags`, `:comp_mags` または `:mag_1_c`, `:mag_1_uc`, `:flux_a` など}

      * `:all_mags`  = 提供されたすべてのスカラー磁力計フィールド（例： `:mag_1_c`, `:mag_1_uc` など）
      * `:comp_mags` = `:mag_1_uc` と `:mag_1_c` の間の提供された補償
  * `vec_terms`:    （オプション）プロットするベクトル磁力計（フラックスゲート）項 {`:all` または `:x`,`:y`,`:z`,`:t`}
  * `ylim`:         （オプション）長さ`2`のプロット `y` 制限（`ymin`,`ymax`） [nT]
  * `dpi`:          （オプション）インチあたりのドット数（画像解像度）
  * `show_plot`:    （オプション）trueの場合、`p1`を表示
  * `save_plot`:    （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:     （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: スカラーまたはベクトル（フラックスゲート）磁力計データのプロット
