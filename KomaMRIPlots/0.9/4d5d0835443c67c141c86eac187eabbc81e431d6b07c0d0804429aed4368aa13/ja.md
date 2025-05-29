```
p = plot_kspace(seq::Sequence; width=nothing, height=nothing, darkmode=false)
```

シーケンス構造体のk空間をプロットします。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# キーワード

  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `height`: (`::Integer`, `=nothing`) プロットの高さ
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) シーケンス構造体のk空間のプロット

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_kspace(seq)
```
