```
p = plot_eddy_currents(seq::Sequence, λ; kwargs...)
```

Sequence構造体の渦電流をプロットします。

# 引数

  * `seq`: (`::Sequence`) Sequence構造体
  * `λ`: (`::Real`, `[s]`) 渦電流の減衰のための時間定数

# キーワード

  * `α`: (`::Vector{Real}`, `=ones(size(λ))`) 渦電流の係数
  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `height`: (`::Integer`, `=nothing`) プロットの高さ
  * `slider`: (`::Bool`, `=true`) スライダーを表示するかどうかを示すブール値
  * `show_seq_blocks`: (`::Bool`, `=false`) シーケンスブロックを表示するかどうかを示すブール値
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値
  * `range`: (`::Vector{Real}`, `=[]`) 最初に表示される時間範囲
  * `title`: (`::String`, `=""`) プロットのタイトル

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) Sequence構造体の渦電流のプロット

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_eddy_currents(seq, 80e-3)
```
