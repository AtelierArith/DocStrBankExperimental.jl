```julia
fast_inv_sqrt(x)
```

The infamous fast inverse square root of `x`, in 32 and 64 bit versions. Can be up to 10x faster than base `1/sqrt(x)`, though with nontrivial loss of precision. The implementations here are good to about 4 ppm.
