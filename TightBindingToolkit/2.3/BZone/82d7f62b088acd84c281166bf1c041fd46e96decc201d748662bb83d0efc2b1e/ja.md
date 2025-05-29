```julia
GetQIndex(Q::Vector{Float64}, bz::BZ ; nearest::Bool = false) --> Vector{Int64}
```

与えられた運動量 `Q` に対応する運動量点の離散化された `BZ` におけるインデックスを返します。入力の `nearest` が `true` に設定されている場合、`Q` がグリッド上に存在しない場合は、`Q` に最も近いグリッド上の運動量点のインデックスを返します。
