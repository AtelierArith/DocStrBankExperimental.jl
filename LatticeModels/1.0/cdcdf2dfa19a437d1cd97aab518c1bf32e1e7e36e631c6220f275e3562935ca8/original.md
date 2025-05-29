```
interaction(f, [T, ]sys, K)
```

Create an `2K`-site interaction operator for a given many-body system. The function `f` takes two `K`-tuples of integer numbers, which are site indices for creation and annihilation operators, and returns the interaction energy.

If the system `sys` has internal degrees of freedom, the function `f` should take four `K`-tuples: first two are site & internal indices for creation operators, and the last two are the same for annihilation operators.
