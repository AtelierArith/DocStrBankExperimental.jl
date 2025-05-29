```julia
RocketModule(
    input_length::Integer,
    n_kernels::Integer
) -> Rocketeer.RocketModule

```

# Summary

Create a new RocketModule structure, requiring feature length and the number of kernels.

# Arguments

  * `input_length::Integer`: the desired length of the kernel features.
  * `n_kernels::Integer`: the desired number of kernels to generate.

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

# Method List / Definition Locations

```julia
RocketModule(input_length, n_kernels)
```

defined at [`packages/Rocketeer/tbPiD/src/lib/rocket.jl:74`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl).
