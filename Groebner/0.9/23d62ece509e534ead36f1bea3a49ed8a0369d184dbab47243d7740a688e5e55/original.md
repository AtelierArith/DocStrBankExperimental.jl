```
WeightedOrdering(weights)
```

Weighted monomial ordering.

Only positive weights are supported.

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# x has weight 3, y has weight 1
ord = WeightedOrdering(x => 3, y => 1)
groebner([x*y + x, x + y^2], ordering=ord)
```
