```
FourierIntegralFunction(f, s, [prototype=nothing]; alias=false)
```

## Arguments

  * `f`: The integrand, accepting inputs `f(x, s(x), p)`
  * `s::AbstractFourierSeries`: The Fourier series to evaluate
  * `prototype`:
  * `alias::Bool`: whether to `deepcopy` the series (false) or use the series as-is (true)
