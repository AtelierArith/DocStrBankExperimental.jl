```
BLUE(model::EFTfitterModel)
```

Calculates the best linear unbiased estimator (BLUE) for multiple  measurements of the same observable, according to https://www.sciencedirect.com/science/article/pii/0168900288900186.

Note: Works only for an `EFTfitterModel` where all measurements have the same observable. If this is not the case, an error is thrown.

Returns a `NamedTuple` with the fields:

  * `:value`: BLUE value
  * `:unc`: BLUE uncertainty
  * `:weights`: Array with the weights for each measurement

Example:

```julia
blue = BLUE(model)
println(blue.value, blue.unc, blue.weights)
```
