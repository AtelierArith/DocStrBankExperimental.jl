```julia
InsertMonopolePair!(lat::Lattice{T}, Monopoles::Vector{Vector{Float64}} ; flux::Float64 = Float64(pi) ) 
```

格子 `lat` に指定された位置 `Monopoles` でモノポール <–> アンチモノポールのペアを挿入し、与えられたフラックス `flux` をディラックを通して挿入します。
