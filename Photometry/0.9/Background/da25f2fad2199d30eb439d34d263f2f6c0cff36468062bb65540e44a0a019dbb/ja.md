```
SourceExtractorBackground()
```

この推定器は、SourceExtractorBackgroundアルゴリズムを使用して入力の背景を返します。

背景は、次の形式のモード推定器を使用して計算されます: `(2.5 * median) - (1.5 * mean)`。

もし `(mean - median) / std > 0.3` であれば中央値が使用され、もし `std = 0` であれば平均が使用されます。

# 例

```jldoctest
julia> data = ones(3, 5);

julia> SourceExtractorBackground()(data)
1.0

julia> SourceExtractorBackground()(data, dims=1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```
