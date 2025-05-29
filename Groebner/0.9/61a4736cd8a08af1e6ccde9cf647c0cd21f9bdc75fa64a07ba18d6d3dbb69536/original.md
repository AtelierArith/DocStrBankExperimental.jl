```
InputOrdering()
```

Preserves the monomial ordering defined on the input polynomials.

This is the default value for the `ordering` keyword argument.

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"]

# Uses the ordering `InputOrdering`, which, in this case, 
# defaults to the lexicographical ordering with x > y
groebner([x*y + x, x + y^2])
```
