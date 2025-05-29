```
update_cx!(nlp, x)
```

Given an `AugLagModel`, if `x != nlp.x`, then updates the internal value `nlp.cx` calling `cons` on `nlp.model`, and reset `nlp.fx` to a NaN. Also updates `nlp.μc_y`.
