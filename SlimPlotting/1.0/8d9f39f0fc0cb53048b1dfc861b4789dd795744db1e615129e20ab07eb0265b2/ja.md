```
plot_fslice(image, spacing; perc=98, cmap=:diverging_bwr_20_95_c54_n256,
            o=(0, 0), interp="hanning", aspect=nothing, d_scale=1.5,
            name="周波数スライス", units="m", new_fig=true, save=nothing)
```

地震データの2D周波数スライスをプロットします。 [`_plot_with_units`](@ref)を呼び出します。

# 引数

  * `image::Array{T, 2}`: プロットする画像
  * `spacing::Tuple`: 物理単位でのグリッド間隔
  * `perc::Int`: (オプション) クリッピングパーセンタイル、デフォルト=95
  * `cmap::Symbol`: (オプション) カラーマップ、デフォルト=:diverging*bwr*20*95*c54_n256
  * `o::Tuple`: (オプション) 画像の原点、デフォルト=(0, 0)
  * `interp::String`: (オプション) 補間方法、デフォルト="hanning"
  * `aspect::Symbol`: (オプション) アスペクト比、デフォルト=:auto
  * `d_scale::Float`: (オプション) 深さスケーリング、デフォルト=1.5。適用されるスケーリングは`(1:max_depth).^d_scale`です。
  * `labels::Tuple`: (オプション) 軸のラベル、デフォルト=(:X, :Depth)
  * `name::String`: (オプション) 図のタイトル、デフォルト="RTM"
  * `units::Tuple(String)`: (オプション) 各軸の物理単位、デフォルト=(:m, :m)。
  * `new_fig::Bool`: (オプション) 新しい図を作成する、デフォルト=true
  * `save::String`: (オプション) 図をファイルに保存する、デフォルト=nothingは図を保存しません
  * `cbar::Bool`: (オプション) カラーバーを表示する、デフォルト=false
