```
p = plot_seqd(seq::Sequence; sampling_params=KomaMRIBase.default_sampling_params())
```

サンプリングされたシーケンス構造体をプロットします。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# キーワード

  * `sampling_params`: (`::Dict{String,Any}()`, `=KomaMRIBase.default_sampling_params()`) サンプリングパラメータの辞書

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) サンプリングされたシーケンス構造体のプロット

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seqd(seq)
```
