```
StdRMS()
```

背景RMS推定のための標準偏差統計を使用します。

# 例

```jldoctest
julia> data = ones(3, 5);

julia> StdRMS()(data)
0.0

julia> StdRMS()(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
