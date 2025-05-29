```
standard_monomials(I::AbstractPolynomialIdeal, vars = variables(I))
```

Return the vector of *standard monomials* in the variables `var` of the ideal `I`. A monomial is a *standard monomial* if it is not the leading monomial of any polynomial of the ideal. If there are infinitely such monomials, `nothing` is returned.

See [CLO5, p. 38], where it is also called *basis monomial*, for more information.

[CLO05] Cox, A. David & Little, John & O'Shea, Donal *Using Algebraic Geometry*. Graduate Texts in Mathematics, **2005**. https://doi.org/10.1007/b138611
