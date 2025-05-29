```
rand(pd::MarginalScalingModel, d::AbstractVector{<:Real}, n::Int=1, ; tags::AbstractVector{<:AbstractString}=String[], x::AbstractVector{<:Real}=Float64[])
```

サイズ `n` のランダムサンプルを、スケーリングモデル `pd` からの期間ベクトル `d` に対して生成します。

### 詳細

期間タグと時間ベクトルは、それぞれキーワード引数 `tags` と `x` で提供できます。
