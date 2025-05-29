```julia
read_td_file(
    td_filepath::AbstractString
) -> Tuple{Int64, Int64, Int64, Vector{Vector{Int64}}, Vector{Vector{Int64}}}

```

PACEフォーマットで記述された木分解インスタンスを解析します。

PACEファイルフォーマットは次のように定義されています: https://pacechallenge.org/2017/treewidth/
