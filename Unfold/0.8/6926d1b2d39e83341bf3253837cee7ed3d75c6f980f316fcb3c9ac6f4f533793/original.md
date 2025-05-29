```julia
coefnames(term)

```

coefnames of a TimeExpandedTerm concatenates the basis-function name with the kronecker product of the term name and the basis-function colnames. Separator is ' : ' Some examples for a firbasis:         basis*313 : (Intercept) : 0.1         basis*313 : (Intercept) : 0.2         basis_313 : (Intercept) : 0.3         ...
