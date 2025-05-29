```
npa_moment(source, level)
```

Constructs the NPA moment matrix at the given level of the hierarchy, taking all degree 1 monomials appearing in `source` as the level 1 operators. `source` can be a monomial, polynomial, or collection containing monomials, polynomials, or sub-collections. The level can be a nonnegative integer or a string, such as `"1 + A B"`.
