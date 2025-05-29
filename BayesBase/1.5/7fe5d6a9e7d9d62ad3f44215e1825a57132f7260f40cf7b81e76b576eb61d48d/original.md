```
PreserveTypeProd{T}
```

`PreserveTypeProd` is one of the strategies for `prod` function. This strategy constraint an output of a prod to be in some specific form. By default it uses the strategy from `default_prod_rule` and converts the output to the prespecified type but can be overwritten  for some distributions for better performance.

See also: [`prod`](@ref), [`ClosedProd`](@ref), [`PreserveTypeLeftProd`](@ref), [`PreserveTypeRightProd`](@ref), [`GenericProd`](@ref)
