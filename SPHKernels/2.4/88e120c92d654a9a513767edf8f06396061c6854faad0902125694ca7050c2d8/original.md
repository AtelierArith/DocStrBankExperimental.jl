```
bias_correction( kernel::Union{WendlandC6_1D{T}, WendlandC6{T}}, 
                 density::Real, m::Real, h_inv::Real, 
                 n_neighbours::Integer ) where T
```

Corrects the density estimate for the kernel bias. See Dehnen&Aly 2012, eq. 18+19.
