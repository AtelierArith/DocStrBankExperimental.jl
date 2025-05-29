# LongMemory.jl

This package provides functions for generating, estimating, and forecasting long memory time series models. Moreover, the package provides plotting capabilities for the different estimators and forecasters, including classical diagnostic plots. 

## Author

[J. Eduardo Vera-Valdés](https://everval.github.io/)

## Documentation

The documentation of the package can be found [here](https://everval.github.io/LongMemory.jl/).

## Quick start

The package includes the classical Nile River and Northern Hemisphere Temperature datasets. They can be accessed by typing:

```julia
NileData()
```

or

```julia
NHTempData()
```

respectively. The package also includes the functions *NileDataPlot()* and *NHTempDataPlot()* to plot the data along with diagnostic plots. The same can be done for an arbitrary data using the *LMPlot()* function.

## Report bugs and suggestions

Please report any bugs or suggestions [here](mailto: eduardo@math.aau.dk)
