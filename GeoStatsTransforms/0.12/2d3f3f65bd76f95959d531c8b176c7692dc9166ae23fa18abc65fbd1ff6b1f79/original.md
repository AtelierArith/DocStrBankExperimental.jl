```
Potrace(mask; [ϵ])
Potrace(mask, var₁ => agg₁, ..., varₙ => aggₙ; [ϵ])
```

Trace polygons on 2D image data with Selinger's Potrace algorithm.

The categories stored in column `mask` are converted into binary masks, which are then traced into multi-polygons. When provided, the option `ϵ` is forwarded to Selinger's simplification algorithm.

Duplicates of a variable `varᵢ` are aggregated with aggregation function `aggᵢ`. If an aggregation function  is not defined for variable `varᵢ`, the default aggregation  function will be used. Default aggregation function is `mean` for continuous variables and `first` otherwise.

# Examples

```julia
Potrace(:mask, ϵ=0.1)
Potrace(1, 1 => last, 2 => maximum)
Potrace(:mask, :a => first, :b => minimum)
Potrace("mask", "a" => last, "b" => maximum)
```

## References

  * Selinger, P. 2003. [Potrace: A polygon-based tracing algorithm](https://potrace.sourceforge.net/potrace.pdf)
