read*con*headers(con::SeisCon, keys::Array{String,1}, blocks::Array{Int,1};                                 prealloc_traces::Int = 50000)

`con`から`blocks`の`keys`を読み取ります。すべてのデータをスキップし、ヘッダーのみを読み取って返します。

# 例

h = read*con*headers(s, ["SourceX"; "SourceY"], Array(1:11))
