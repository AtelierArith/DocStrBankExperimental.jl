```
prednames(<term>)
```

予測因子の名前を返します。返り値は `String`、`String` の iterable、または `nothing` です。

# 例

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
