```
optblocklength(data, bi::BootInput)::Float64
optblocklength(data ; kwargs...)::Float64
```

Provides an estimate of the optimal block-length to use with a dependent bootstrap.

For multivariate datasets, optimal block length is estimated for each column of data, and then bi.fblocklengthcombine, which is a function that maps Vector{Float64} to Float64, is called to reduce the multiple estimates to a single estimates. The default value for fblocklengthcombine is median.

Block length methods currently implemented include: 

```
 - Patton, Politis, White (2009) "Correction to Automatic Block Length Selection For the Dependent Bootstrap"
```

For all methods discussed above, bandwidth is estimated following Politis (2003) "Adaptive Bandwidth Choice", using the flat-top kernel suggested in that paper.
