```
isolate_variable(poly::_APL, var::AbstractVariable, mutability::MA.MutableTrait)
```

Returns a polynomial with variable `var`. The other variables of `poly` are moved as coefficients.

The output can be mutated without affecting `poly` if `mutability` is `MA.IsNotMutable`.
