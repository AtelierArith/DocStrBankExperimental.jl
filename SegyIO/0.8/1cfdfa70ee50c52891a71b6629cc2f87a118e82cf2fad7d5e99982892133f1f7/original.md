extract*con*headers(con::SeisCon, keys::Array{String,1}, blocks::Array{Int,1};                                 prealloc_traces::Int = 50000)

Read `keys` from `blocks` in `con`. Skips all data and only reads and returns headers in an array. This method is similar to `read_con_headers`, except the data is returned

# Examples

h = extract*con*headers(s, ["SourceX"; "SourceY"], Array(1:11))
