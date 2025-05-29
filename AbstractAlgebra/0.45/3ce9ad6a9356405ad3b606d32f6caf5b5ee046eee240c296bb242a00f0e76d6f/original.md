```
reverse(x::PolynomialElem, len::Int)
```

Return the reverse of the polynomial $x$, thought of as a polynomial of the given length (the polynomial will be notionally truncated or padded with zeroes before the leading term if necessary to match the specified length). The resulting polynomial is normalised. If `len` is negative we throw a `DomainError()`.
