```
add_to_expression!(expression, terms...)
```

Updates `expression` *in place* to `expression + (*)(terms...)`. This is typically much more efficient than `expression += (*)(terms...)`. For example, `add_to_expression!(expression, a, b)` produces the same result as `expression += a*b`, and `add_to_expression!(expression, a)` produces the same result as `expression += a`.

Only a few methods are defined, mostly for internal use, and only for the cases when (1) they can be implemented efficiently and (2) `expression` is capable of storing the result. For example, `add_to_expression!(::AffExpr, ::VariableRef, ::VariableRef)` is not defined because a `GenericAffExpr` cannot store the product of two variables.
