# サイズメソッド

```julia
size(ts::TSFrame)
```

`ts`の行数と列数をタプルとして返します。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> TSFrames.size(TSFrame([collect(1:100) collect(1:100) collect(1:100)]))
(100, 3)
```
