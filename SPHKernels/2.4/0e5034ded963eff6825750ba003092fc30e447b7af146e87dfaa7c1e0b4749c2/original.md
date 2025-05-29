```
bias_correction( kernel::Union{WendlandC4_1D{T}, WendlandC4{T}}, 
                 density::Real, m::Real, h_inv::Real, 
                 n_neighbours::Int64 ) where T
```

Corrects the density estimate for the kernel bias. See Dehnen&Aly 2012, eq. 18+19.
