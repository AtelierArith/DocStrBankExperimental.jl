```
bias_correction( kernel::Union{WendlandC6_1D{T}, WendlandC6{T}}, 
                 density::Real, m::Real, h_inv::Real, 
                 n_neighbours::Integer ) where T
```

カーネルバイアスの密度推定を修正します。Dehnen&Aly 2012、式18+19を参照してください。
