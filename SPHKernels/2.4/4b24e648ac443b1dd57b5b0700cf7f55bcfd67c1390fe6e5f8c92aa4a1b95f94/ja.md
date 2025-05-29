```
bias_correction( kernel::Union{WendlandC2_1D{T}, WendlandC2{T}}, 
                 density::Real, m::Real, h_inv::Real,
                 n_neighbours::Integer ) where T
```

カーネルバイアスのために密度推定を修正します。Dehnen&Aly 2012、式18+19を参照してください。
