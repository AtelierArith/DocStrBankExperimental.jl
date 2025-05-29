```
apply(gate::StaticGate, pstr, coeff, theta)
```

Calling apply on a `StaticGate` will dispatch to a 3-argument apply function without the paramter `theta`. If a 4-argument apply function is defined for a concrete type, it will still dispatch to that one. See the `4-custom-gates.ipynb` for examples of how to define custom gates.
