```
p = plot_seq(seq::Sequence; kwargs...)
```

シーケンス構造体をプロットします。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# キーワード

  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `height`: (`::Integer`, `=nothing`) プロットの高さ
  * `slider`: (`::Bool`, `=true`) スライダーを表示するかどうかを示すブール値
  * `show_seq_blocks`: (`::Bool`, `=false`) シーケンスブロックを表示するかどうかを示すブール値
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値
  * `range`: (`::Vector{Real}`, `=[]`) 最初に表示される時間範囲
  * `title`: (`::String`, `=""`) プロットのタイトル
  * `freq_in_phase`: (`::Bool`, `=true`) RF位相にFM変調を含める
  * `gl`: (`::Bool`, `=false`) `PlotlyJS.scattergl` バックエンドを使用する（高速）
  * `max_rf_samples`: (`::Integer`, `=100`) 最大RFサンプル数
  * `show_adc`: (`::Bool`, `=false`) マーカー付きでADCサンプルをプロットする

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) シーケンス構造体のプロット

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seq(seq)
```
