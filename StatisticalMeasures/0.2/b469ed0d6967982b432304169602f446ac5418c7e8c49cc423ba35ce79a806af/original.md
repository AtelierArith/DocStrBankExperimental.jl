```
RSquared()
```

Return a callable measure for computing the R² coefficient. Aliases: `rsq`, `rsquared`.

```
RSquared()(ŷ, y)
```

Evaluate `RSquared()` on predictions `ŷ`, given ground truth observations `y`. Specifically, return the value of

$1 - \frac{∑ᵢ (ŷ_i- y_i)^2}{∑ᵢ ȳ - y_i)^2},$

where $ȳ$ denote the mean of the $y_i$. Also known as R-squared or the coefficient of determination, the `R²` coefficients is suitable for interpreting linear regression analysis (Chicco et al., [2021](https://doi.org/10.7717/peerj-cs.623)).

Generally, an observation `obs` in `MLUtils.eachobs(y)` is expected to satisfy `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`. 

For a complete dictionary of available measures, keyed on constructor, run [`measures()`](@ref). 

# Traits

```
consumes_multiple_observations = true
can_report_unaggregated = false
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = false
supports_class_weights = false
orientation = StatisticalMeasuresBase.Score()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = R² coefficient
```
