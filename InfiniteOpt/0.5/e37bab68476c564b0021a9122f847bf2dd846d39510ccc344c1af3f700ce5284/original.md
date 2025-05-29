```
has_derivative_constraints(dref::DerivativeRef)::Bool
```

Return a `Bool` whether `dref` has been evaluated within the `InfiniteModel` and  has derivative constraints that have been added to the `InfiniteModel`. Note this  does not indicate if such constraints have been added to the optimizer model. Thus,  with normal usage (i.e., not using `evaluate`) this should always return `false`.
