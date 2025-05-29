```
RelativePermeabilities((kr1, kr2, ...))
```

A simple relative permeability implementation. Assumes that each phase has a relative permeability on the form:

$K_{r,phase} = F(S_{phase})$

Supports multiple fluid regions through the `regions` keyword.

# Examples

Single region:

```
kr1 = S -> S^2
kr2 = S -> S^3

kr = RelativePermeabilities((kr1, kr2))
```

Two regions:

```
kr1_reg1 = S -> S^2
kr2_reg1 = S -> S^3

kr1_reg2 = S -> S^3
kr2_reg2 = S -> S^4

regions # should be a vector with one entry that is 1 or 2 for each cell in the domain

kr = RelativePermeabilities(((kr1_reg1, kr2_reg1), (kr1_reg2, kr2_reg2)), regions = regions)
```
