```
seq = read_seq(filename)
```

`.seq` 拡張子を持つ Pulseq ファイルから Sequence 構造体を返します。

# 引数

  * `filename`: (`::String`) シーケンスファイル `.seq` の絶対パスまたは相対パス

# 返り値

  * `seq`: (`::Sequence`) Sequence 構造体

# 例

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/spiral.seq")

julia> seq = read_seq(seq_file)

julia> plot_seq(seq)
```
