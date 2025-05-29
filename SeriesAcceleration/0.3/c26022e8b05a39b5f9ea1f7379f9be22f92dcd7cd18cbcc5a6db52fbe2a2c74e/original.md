```
Richardson <: SumHelper
```

## Desciption

Richardson method helper. This struct is initialized with a range of integers `dom` and a list of exponents `exponents`, which are used internally. More exponents can lead to better convergence at the cost of noise. There are two methods available for the fitting of internal weights: `:bender`, `:rohringer`. See C. Bender, A. Orszag 99, p. 375; G. Rohringer, A. Toschi 2016 for the derivation Due to the different fit methods, `method=:bender` will not use 

## Usage

## Fields

  * **`indices`**    : `AbstractVector{Int}` of indices of partial sum array which have been fitted
  * **`weights`**    : `Matrix{Float64}` fit weights
