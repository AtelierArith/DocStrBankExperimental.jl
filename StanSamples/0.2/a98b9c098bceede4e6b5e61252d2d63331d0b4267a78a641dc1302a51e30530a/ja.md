```julia
read_sample_matrix(filename)

```

CSVファイルまたは`IO`ストリームからStanサンプルを読み込みます。ヘッダー（変数名を含む文字列のベクター）とサンプルを`AbstractMatrix{Float64}`として返します。

```jldoctest julia> io = IOBuffer("a,b.1,b.2,c.1.1,c.2.1,c.1.2,c.2.2 " *        "1.0,2.0,3.0,4.0,5.0,6.0,7.0 " *        "8.0,9.0,10.0,11.0,12.0,13.0,14.0");

julia> header, matrix = read*sample*matrix(io);

julia> header 7-element Vector{SubString{String}}:  "a"  "b.1"  "b.2"  "c.1.1"  "c.2.1"  "c.1.2"  "c.2.2"

julia> matrix 2×7 Matrix{Float64}:  1.0  2.0   3.0   4.0   5.0   6.0   7.0  8.0  9.0  10.0  11.0  12.0  13.0  14.0
```
