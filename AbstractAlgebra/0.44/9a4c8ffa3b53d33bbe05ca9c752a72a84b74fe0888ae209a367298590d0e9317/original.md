```
length(a::PolynomialElem)
```

Return the length of the polynomial. The length of a univariate polynomial is defined to be the number of coefficients in its dense representation, including zero coefficients. Thus naturally the zero polynomial has length zero and additionally for nonzero polynomials the length is one more than the degree. (Note that the leading coefficient will always be nonzero.)
