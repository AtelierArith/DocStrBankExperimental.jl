```
abstract type ExprOp{T, N}
```

the abstract type of operators, `T` is `Pure` or `Mixed` and `N` is an `Int` for generic operators (the number of sites on which the operator may apply) and `IndexOp` for indexed operators

```
SimpleOp = ExprOp{Pure, 1}
ExprIndexed{T} = ExprOp{T, IndexOp}
```
