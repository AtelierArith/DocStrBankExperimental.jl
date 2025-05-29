```
p = plot_phantom_map(obj::Phantom, key::Symbol; kwargs...)
```

特定のスピンパラメータによるファントムマップをプロットします。`key`で指定されます。

# 引数

  * `obj`: (`::Phantom`) ファントム構造体
  * `key`: (`::Symbol`, opts: [`:ρ`, `:T1`, `:T2`, `:T2s`, `:x`, `:y`, `:z`]) ファントムスピンの異なるパラメータを表示するためのシンボル

# キーワード

  * `height`: (`::Integer`, `=600`) プロットの高さ
  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値
  * `view_2d`: (`::Bool`, `=false`) 2D散布図を使用するかどうかを示すブール値
  * `colorbar`: (`::Bool`, `=true`) カラーバーを表示するかどうかを示すブール値
  * `max_spins`:(`::Int`, `=100_000`) 表示されるスピンの最大数
  * `time_samples`:(`::Int`, `=0`) 動きの`t_start`と`t_end`の間の中間時間サンプル
  * `frame_duration_ms`:(`::Int`, `=250`) 2つのフレーム間のミリ秒単位の時間

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) 特定のスピンパラメータに対するファントムマップのプロット

# 参考文献

Colormaps from https://github.com/markgriswold/MRFColormaps Towards Unified Colormaps for Quantitative MRF Data, Mark Griswold, et al. (2018).

# 例

```julia-repl
julia> obj2D, obj3D = brain_phantom2D(), brain_phantom3D();

julia> plot_phantom_map(obj2D, :ρ)

julia> plot_phantom_map(obj3D, :ρ)
```
