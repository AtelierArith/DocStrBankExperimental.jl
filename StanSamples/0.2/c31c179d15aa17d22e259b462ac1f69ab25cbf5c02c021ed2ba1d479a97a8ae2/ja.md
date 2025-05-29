```julia
read_samples(filename)

```

CSVファイルまたは`IO`ストリームからStanサンプルを読み込みます。

変数名をプロパティとしてアクセスできる配列のコンテナを返します（実際には現在の実装である`NamedTuple`のようなものですが、将来的に変更される可能性があります）。各配列は変数のサンプルを持ち、最後のインデックスは各描画ごとに異なります。

```jldoctest
julia> io = IOBuffer("a,b.1,b.2,c.1.1,c.2.1,c.1.2,c.2.2
" *
                     "1.0,2.0,3.0,4.0,5.0,6.0,7.0
" *
                     "8.0,9.0,10.0,11.0,12.0,13.0,14.0");

julia> samples = read_samples(io);

julia> samples.a
2-element Array{Float64,1}:
 1.0
 8.0

julia> samples.b
2×2 ElasticArrays.ElasticArray{Float64,2,1}:
 2.0   9.0
 3.0  10.0

julia> samples.c
2×2×2 ElasticArrays.ElasticArray{Float64,3,2}:
[:, :, 1] =
 4.0  6.0
 5.0  7.0

[:, :, 2] =
 11.0  13.0
 12.0  14.0
```
