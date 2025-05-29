```
GenericProd
```

`GenericProd` is one of the strategies for `prod` function. This strategy does always produces a result,  even if the closed form product is not availble, in which case simply returns the `ProductOf` object. `GenericProd` sometimes  fallbacks to the `default_prod_rule` which it may or may not use under some circumstances.  For example if the `default_prod_rule` is `ClosedProd` - `GenericProd` will try to optimize the tree with  analytical closed solutions (if possible).

See also: [`prod`](@ref), [`ProductOf`](@ref), [`ClosedProd`](@ref), [`PreserveTypeProd`](@ref), [`default_prod_rule`](@ref)
