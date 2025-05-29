```
Lex()
Lex(variables)
Lex(variables...)
```

Lexicographical monomial ordering.

We use the definition from Chapter 1, Computational Commutative Algebra 1, by Martin Kreuzer, Lorenzo Robbiano. DOI: https://doi.org/10.1007/978-3-540-70628-1.

*Dura Lex, sed Lex.*

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# Lexicographical ordering with x > y
groebner([x*y + x, x + y^2], ordering=Lex())

# Lexicographical ordering with y > x
groebner([x*y + x, x + y^2], ordering=Lex([y, x]))

# Lexicographical ordering with x > y
# Both syntax are allowed -- Lex([...]) and Lex(...)
groebner([x*y + x, x + y^2], ordering=Lex(x, y))
```
