```
complex_normal_form(a::CalciumFieldElem, deep::Bool=true)
```

Returns the input rewritten using standardizing transformations over the complex numbers:

  * Elementary functions are rewritten in terms of exponentials, roots and logarithms.
  * Complex parts are rewritten using logarithms, square roots, and (deep) complex conjugates.
  * Algebraic numbers are rewritten in terms of cyclotomic fields where applicable.

If deep is set, the rewriting is applied recursively to the tower of extension numbers; otherwise, the rewriting is only applied to the top-level extension numbers.

The result is not a normal form in the strong sense (the same number can have many possible representations even after applying this transformation), but this transformation can nevertheless be a useful heuristic for simplification.
