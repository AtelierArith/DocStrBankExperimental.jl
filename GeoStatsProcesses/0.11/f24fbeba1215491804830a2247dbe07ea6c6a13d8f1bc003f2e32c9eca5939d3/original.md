```
FFTSIM(; [options])
```

The FFT simulation method introduced by Oliver 1995 and Ravalec 2000.

The covariance function is perturbed in the frequency domain after a fast Fourier transform. White noise is added to the phase of the spectrum, and a realization is produced by an inverse Fourier transform.

Data conditioning is currently performed with Kriging, which accepts the following neighbor search options.

## Options

  * `minneighbors` - Minimum number of neighbors (default to `1`)
  * `maxneighbors` - Maximum number of neighbors (default to `26`)
  * `neighborhood` - Search neighborhood (default to `nothing`)
  * `distance`     - Distance used to find nearest neighbors (default to `Euclidean()`)

## References

  * Oliver 1995. [Moving averages for Gaussian simulation in two and three dimensions](https://link.springer.com/article/10.1007/BF02091660)
  * Ravalec et al. 2000. [The FFT Moving Average (FFT-MA) Generator: An Efficient Numerical Method for Generating and Conditioning Gaussian Simulations](https://link.springer.com/article/10.1023/A:1007542406333)
  * Figueiredo et al. 2019. [Revisited Formulation and Applications of FFT Moving Average](https://link.springer.com/article/10.1007/s11004-019-09826-4)

### Notes

The method is limited to simulations on regular grids, and care must be taken to make sure that the correlation length is small enough compared to the grid size. As a general rule of thumb, avoid correlation lengths greater than 1/3 of the grid.

Visual artifacts can appear near the boundaries of the grid if the correlation length is large compared to the grid itself.
