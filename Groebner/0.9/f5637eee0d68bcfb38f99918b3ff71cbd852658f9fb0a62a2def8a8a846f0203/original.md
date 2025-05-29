```
ProductOrdering(ord1, ord2)
```

Product monomial ordering. Compares by `ord1`, breaks ties by `ord2`.

Can also be constructed with `*`.

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, w) = QQ["x", "y", "z", "w"];

# Ordering with x, y > w, z
ord = ProductOrdering(DegRevLex(x, y), DegRevLex(w, z))
groebner([x*y + w, y*z - w], ordering=ord)
```

It is possible to use the `*` operator:

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, t) = QQ["x", "y", "z", "t"];

ord1 = Lex(t)
ord2 = DegRevLex(x, y, z)
# t >> x, y, z
ord = ord1 * ord2
groebner([x*y*z + z, t * z - 1], ordering=ord)
```
