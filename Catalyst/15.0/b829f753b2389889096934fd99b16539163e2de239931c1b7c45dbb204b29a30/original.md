```
iscomplexbalanced(rs::ReactionSystem, parametermap; sparse = false)
```

Constructively compute whether a network will have complex-balanced equilibrium solutions, following the method in van der Schaft et al., [2015](https://link.springer.com/article/10.1007/s10910-015-0498-2#Sec3).

Requires the specification of values for the parameters/rate constants. Accepts a dictionary, vector, or tuple of parameter-to-value mappings, e.g. [k1 => 1.0, k2 => 2.0,...].
