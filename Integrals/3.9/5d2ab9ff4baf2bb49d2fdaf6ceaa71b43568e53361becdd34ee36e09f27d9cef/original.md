```
VEGAS(; nbins = 100, ncalls = 1000, debug=false)
```

Multidimensional adaptive Monte Carlo integration from MonteCarloIntegration.jl. Importance sampling is used to reduce variance. This method also takes three optional arguments `nbins`, `ncalls` and `debug` which are the initial number of bins each dimension of the integration domain is divided into, the number of function calls per iteration of the algorithm, and whether debug info should be printed, respectively.

## References

@article{lepage1978new, title={A new algorithm for adaptive multidimensional integration}, author={Lepage, G Peter}, journal={Journal of Computational Physics}, volume={27}, number={2}, pages={192–203}, year={1978}, publisher={Elsevier} }
