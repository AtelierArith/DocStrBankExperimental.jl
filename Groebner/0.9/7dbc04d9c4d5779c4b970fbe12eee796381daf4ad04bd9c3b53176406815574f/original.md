```
DegLex()
DegLex(variables)
DegLex(variables...)
```

Degree lexicographical monomial ordering.

We use the definition from Chapter 1, Computational Commutative Algebra 1, by Martin Kreuzer, Lorenzo Robbiano. DOI: https://doi.org/10.1007/978-3-540-70628-1.

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# Degree lexicographical ordering with x > y
groebner([x*y + x, x + y^2], ordering=DegLex())

# Degree lexicographical ordering with y > x
groebner([x*y + x, x + y^2], ordering=DegLex([y, x]))
```
