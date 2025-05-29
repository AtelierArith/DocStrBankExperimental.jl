```
HCubatureJL(; norm=norm, initdiv=1, buffer = nothing)
```

Multidimensional "h-adaptive" integration from HCubature.jl. This method also takes the optional arguments `initdiv` and `norm`. Which are the initial number of segments each dimension of the integration domain is divided into, and the norm for calculating the error, respectively. Lastly, the `buffer` keyword, if set (e.g. `buffer=true`), will allocate a buffer to reuse for multiple integrals and may require evaluating the integrand unless an `integrand_prototype` is provided. Unlike the `buffer` keyword to `hcubature/hquadrature`, you do not allocate the buffer as this is handled automatically.

## References

```tex
@article{genz1980remarks,
title={Remarks on algorithm 006: An adaptive algorithm for numerical integration over an N-dimensional rectangular region},
author={Genz, Alan C and Malik, Aftab Ahmad},
journal={Journal of Computational and Applied mathematics},
volume={6},
number={4},
pages={295--302},
year={1980},
publisher={Elsevier}
}
```
