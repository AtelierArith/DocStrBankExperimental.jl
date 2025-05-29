```
get_lipschitz(model)
```

Extract Lipschitz bound from a Lipschitz-bounded model

Returns Lipschitz bound as a float. Function only works on the following types:

  * `LBDN` and `DiffLBDN`
  * `DenseLBDNParams` and `DirectLBDNParams`
  * `LipschitzRENParams`
