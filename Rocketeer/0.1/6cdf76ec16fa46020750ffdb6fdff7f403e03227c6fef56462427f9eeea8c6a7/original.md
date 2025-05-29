```julia
struct RocketKernel
```

# Summary

Structure containing information about one Rocket kernel.

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

  * `length::Int64`: The length of the kernel.

  * `weight::Vector{Float64}`: The vector of weights corresponding to the features.

  * `bias::Float64`: The internal Rocket bias parameter, computed during construction.

  * `dilation::Int64`: The internal Rocket dilation parameter, computed during construction.

  * `padding::Int64`: The internal Rocket padding parameter, computed during construction.
