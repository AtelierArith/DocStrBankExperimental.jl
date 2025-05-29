```
prednames(<term>)
```

Return the name(s) of predictor(s). Return value is either a `String`, an iterable of `String`s or `nothing`.

# Examples

```julia
julia> iris = dataset("datasets", "iris");

julia> f = formula(lm(@formula(log(SepalLength) ~ SepalWidth + PetalLength * PetalWidth), iris))
FormulaTerm
Response:
  (SepalLength)->log(SepalLength)
Predictors:
  1
  SepalWidth(continuous)
  PetalLength(continuous)
  PetalWidth(continuous)
  PetalLength(continuous) & PetalWidth(continuous)

julia> prednames(f)
["(Intercept)", "SepalWidth", "PetalLength", "PetalWidth", "PetalLength & PetalWidth"]

julia> prednames(InterceptTerm{false}())


```
