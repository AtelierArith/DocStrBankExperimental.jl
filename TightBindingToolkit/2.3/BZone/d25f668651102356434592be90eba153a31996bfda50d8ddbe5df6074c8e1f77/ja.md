```julia
CombinedIndexPath(bz::BZ, points::Vector{Vector{Float64}} ; nearest::Bool = false, closed::Bool = true) --> Vector{Vector{Int64}}
```

与えられた `points` に存在する点を結ぶインデックス空間のパスを返します。これは point[1] –> point[2] –> ... –> point[end] –> point[1] となります。オプションの入力 `nearest` は [`GetQIndex`](@ref) と同じで、`closed` はパスが閉じたループであるかどうかを決定します。
