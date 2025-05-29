```
DE_BFD()
DE_BFD([wp,] kl, kc)
```

Construct a metric using the BFD equation, with weighting parameters `kl` and `kc`. Additionally, a whitepoint `wp` can be specified, because the BFD equation must convert between `XYZ` and `Lab` during the computation. When not provided, `kl` and `kc` default to `1`, and `wp` defaults to CIE D65 (`Colors.WP_D65`).
