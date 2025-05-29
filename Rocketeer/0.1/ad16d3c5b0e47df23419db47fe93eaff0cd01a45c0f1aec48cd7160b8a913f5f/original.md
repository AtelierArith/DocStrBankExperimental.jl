```julia
struct RocketModule
```

# Summary

Structure containing a vector of [`RocketKernel`](@ref)s.

# Attribution

## Programmer

  * Sasha Petrenko <petrenkos@mst.edu> [@AP6YC](https://github.com/AP6YC)

## Original Authors

  * Angus Dempster
  * Francois Petitjean
  * Geoff Webb

## Bibtex Entry

```bibtex
@article{dempster_etal_2020,
    author  = {Dempster, Angus and Petitjean, Francois and Webb, Geoffrey I},
    title   = {ROCKET: Exceptionally fast and accurate time classification using random convolutional kernels},
    year    = {2020},
    journal = {Data Mining and Knowledge Discovery},
    doi     = {https://doi.org/10.1007/s10618-020-00701-z}
}
```

## Citation Links

  * Papers:

      * [Journal article](https://link.springer.com/article/10.1007/s10618-020-00701-z) ([DOI](https://doi.org/10.1007/s10618-020-00701-z))
      * [Preprint](https://arxiv.org/abs/1910.13051)
  * Software

      * [rocket](https://github.com/angus924/rocket) (Python)

# Fields

  * `input_length::Int64`: The input length used to generate the [`RocketKernel`](@ref)s.

  * `kernels::Vector{Rocketeer.RocketKernel}`: The list of [`RocketKernel`](@ref)s constituting a full Rocket module.
