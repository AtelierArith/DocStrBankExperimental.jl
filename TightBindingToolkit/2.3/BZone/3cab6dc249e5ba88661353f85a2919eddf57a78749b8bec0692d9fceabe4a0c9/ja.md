```julia
CombinedBZPath(bz::BZ, points::Vector{Vector{Float64}} ; nearest::Bool = false, closed::Bool = true) --> Vector{Vector{Float64}}
```

与えられた運動量点 `points` に存在する点を結ぶ運動量空間の離散化された `BZ` のパスを返します。これは point[1] –> point[2] –> ... –> point[end] –> point[1] という形になります。オプションの入力 `nearest` は [`GetQIndex`](@ref) と同じで、`closed` はパスが閉じたループであるかどうかを決定します。
