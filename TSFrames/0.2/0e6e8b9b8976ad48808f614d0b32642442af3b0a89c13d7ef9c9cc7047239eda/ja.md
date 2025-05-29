# 最初の行

```julia
first(ts::TSFrame)
```

`ts`の最初の行をTSFrameオブジェクトとして返します。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random)
julia> first(TSFrame(1:10))
(10 x 1) TSFrame with Dates.Date Index

 Index       x1
 Date        Float64
───────────────────────
 2022-02-01  0.768448

```
