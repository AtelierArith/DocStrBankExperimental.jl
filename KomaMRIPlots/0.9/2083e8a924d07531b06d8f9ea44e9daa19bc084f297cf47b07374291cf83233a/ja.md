```
p = plot_signal(raw::RawAcquisitionData; kwargs...)
```

ISMRMRD形式の生信号をプロットします。

# 引数

  * `raw`: (`::RawAcquisitionData`) RawAcquisitionData構造体（ISMRMRD形式の生信号）

# キーワード

  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `height`: (`::Integer`, `=nothing`) プロットの高さ
  * `slider`: (`::Bool`, `=true`) スライダーを表示するかどうかを示すブール値
  * `show_sim_blocks`: (`::Bool`, `=false`) シーケンスブロックを表示するかどうかを示すブール値
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値
  * `range`: (`::Vector{Real}`, `=[]`) 最初に表示される時間範囲

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) 生信号のプロット

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/5.koma_paper/comparison_accuracy/sequences/EPI/epi_100x100_TE100_FOV230.seq");

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> raw = simulate(obj, seq, sys)

julia> plot_signal(raw)
```
