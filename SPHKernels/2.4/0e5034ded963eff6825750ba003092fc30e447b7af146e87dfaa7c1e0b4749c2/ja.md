```
bias_correction( kernel::Union{WendlandC4_1D{T}, WendlandC4{T}}, 
                 density::Real, m::Real, h_inv::Real, 
                 n_neighbours::Int64 ) where T
```

カーネルバイアスのために密度推定を修正します。Dehnen&Aly 2012、式18+19を参照してください。
