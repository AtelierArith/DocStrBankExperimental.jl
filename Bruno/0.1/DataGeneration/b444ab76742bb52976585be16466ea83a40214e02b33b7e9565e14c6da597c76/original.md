```
opt_block_length(array, bootstrap_method::TSBootMethod)
```

Computes the optimal block length for a time series block bootstrap using the methods defined  by Politis and White (2004). 

If bootstrap method other than Stationary or CircularBlock is used, the function defaults  to CircularBlock

# Examples

```julia
using Distributions: Normal

# create ar(1) data set
ar1 = [1.0];
for _ in 1:799
    push!(ar1, ar1[end] * 0.7 + rand(Normal()))
    end

# find optimal block lengths
st_bl = opt_block_length(ar1, Stationary)
cb_bl = opt_block_length(ar1, CircularBlock)
```
