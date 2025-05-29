# サイズメソッド

```julia
ncol(ts::TSFrame)
```

`ts`の列数を返します。`nc`は`ncol`のエイリアスです。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;

julia> random(x) = rand(MersenneTwister(123), x);

julia> TSFrames.ncol(TSFrame([random(100) random(100) random(100)]))
3

julia> nc(TSFrame([random(100) random(100) random(100)]))
3
```
