extract*con*headers(con::SeisCon, keys::Array{String,1}, blocks::Array{Int,1};                                 prealloc_traces::Int = 50000)

`con`から`blocks`の`keys`を読み取ります。すべてのデータをスキップし、ヘッダーのみを配列として読み取り、返します。このメソッドは`read_con_headers`に似ていますが、データが返されます。

# 例

h = extract*con*headers(s, ["SourceX"; "SourceY"], Array(1:11))
