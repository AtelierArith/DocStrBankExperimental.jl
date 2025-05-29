Main module for the `Rocketeer.jl` package.

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

# Imports

The following names are imported by the package as dependencies:

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `NumericalTypeAliases`
  * `Pkg`
  * `Random`

# Exports

The following names are exported and available when `using` the package:

  * [`ROCKETEER_VERSION`](@ref)
  * [`RocketKernel`](@ref)
  * [`RocketModule`](@ref)
  * [`apply_kernel`](@ref)
  * [`apply_kernels`](@ref)
  * [`load_rocket`](@ref)
  * [`save_rocket`](@ref)
