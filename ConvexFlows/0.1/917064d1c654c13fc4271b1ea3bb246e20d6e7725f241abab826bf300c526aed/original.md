```
Ubar(obj::Objective, ν)
```

Evaluates the 'conjugate' of the net flow utility function `objective` at `ν`. Specifically,

$$
    \bar U(\nu) = \sup_y \left(U(y) - \nu^T y \right).
$$
