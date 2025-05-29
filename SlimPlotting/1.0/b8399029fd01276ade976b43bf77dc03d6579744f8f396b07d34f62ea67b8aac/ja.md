```
plot_simage(image, spacing; perc=98, cmap=:linear_grey_10_95_c0_n256,
            o=(0, 0), interp="hanning", aspect=nothing, d_scale=1.5,
            labels=(:X, :Depth), name="RTM", units=(:m, :m), new_fig=true,
            save=nothing, cbar=false)
```

2D地震画像をグリッド間隔`spacing`でプロットします。[`_plot_with_units`](@ref)を呼び出します。

# 引数

  * `image::Array{T, 2}`: プロットする画像
  * `spacing::Tuple`: 物理単位でのグリッド間隔
  * `perc::Int`: (オプション) クリッピングパーセンタイル、デフォルト=95
  * `cmap::Symbol`: (オプション) カラーマップ、デフォルト=:linear*grey*10*95*c0_n256
  * `o::Tuple`: (オプション) 画像の原点、デフォルト=(0, 0)
  * `interp::String`: (オプション) 補間方法、デフォルト="hanning"
  * `aspect::Symbol`: (オプション) アスペクト比、デフォルト=:auto
  * `d_scale::Float`: (オプション) 深さスケーリング、デフォルト=1.5。適用されるスケーリングは`(1:max_depth).^d_scale`です。
  * `labels::Tuple`: (オプション) 軸のラベル、デフォルト=(:X, :Depth)
  * `name::String`: (オプション) 図のタイトル、デフォルト="RTM"
  * `units::Tuple(String)`: (オプション) 各軸の物理単位、デフォルト=(:m, :m)。
  * `new_fig::Bool`: (オプション) 新しい図を作成する、デフォルト=true
  * `save::String`: (オプション) 図をファイルに保存、デフォルト=nothingは図を保存しません
  * `cbar::Bool`: (オプション) カラーバーを表示する、デフォルト=false
