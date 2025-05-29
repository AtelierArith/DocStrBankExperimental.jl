```
DegRevLex()
DegRevLex(variables)
DegRevLex(variables...)
```

Degree reverse lexicographical monomial ordering.

We use the definition from Chapter 1, Computational Commutative Algebra 1, by Martin Kreuzer, Lorenzo Robbiano. DOI: https://doi.org/10.1007/978-3-540-70628-1.

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# Degree reverse lexicographical ordering with x > y
groebner([x*y + x, x + y^2], ordering=DegRevLex())

# Degree reverse lexicographical ordering with y > x
groebner([x*y + x, x + y^2], ordering=DegRevLex(y, x))
```
