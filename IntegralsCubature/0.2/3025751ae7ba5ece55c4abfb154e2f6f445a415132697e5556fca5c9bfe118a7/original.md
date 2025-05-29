```
CubatureJLh()
```

Multidimensional h-adaptive integration from Cubature.jl. `error_norm` specifies the convergence criterion  for vector valued integrands. Defaults to `Cubature.INDIVIDUAL`, other options are `Cubature.PAIRED`, `Cubature.L1`, `Cubature.L2`, or `Cubature.LINF`.

## References

@article{genz1980remarks, title={Remarks on algorithm 006: An adaptive algorithm for numerical integration over an N-dimensional rectangular region}, author={Genz, Alan C and Malik, Aftab Ahmad}, journal={Journal of Computational and Applied mathematics}, volume={6}, number={4}, pages={295–302}, year={1980}, publisher={Elsevier} }
