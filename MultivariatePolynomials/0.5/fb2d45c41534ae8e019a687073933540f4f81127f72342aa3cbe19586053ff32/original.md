Returns a polynomial with the terms having their monomial in the monomial vector `mv` removed in the polynomial `p`.

### Examples

Calling `remove_monomials(4x^2*y + x*y + 2x, [x*y])` should return $4x^2*y + 2x$.
