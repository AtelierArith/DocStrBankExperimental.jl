# サイズメソッド

```julia
nrow(ts::TSFrame)
nr(ts::TSFrame)
```

`ts`の行数を返します。`nr`は`nrow`のエイリアスです。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> ts = TSFrame(collect(1:10))
julia> TSFrames.nrow(ts)
10
```
