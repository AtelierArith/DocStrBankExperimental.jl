```
pow(a::CalciumFieldElem, b::Int; form::Symbol=:default)
```

Return *a* raised to the integer power `b`. The optional `form` argument allows specifying the representation. In `:default` form, this is equivalent to `a ^ b`, which may create a new extension number $a^b$ if the exponent `b` is too large (as determined by the parent option `:pow_limit` or `:prec_limit` depending on the case). In `:arithmetic` form, the exponentiation is performed arithmetically in the field of `a`, regardless of the size of the exponent `b`.
