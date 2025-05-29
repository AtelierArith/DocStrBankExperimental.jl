```
jacobianPOE(q, xi, T)
```

Returns The jacobian in 1) the base frame, 2) the tool frame and returns the FK. It must be handed a precomputed end transform `Tend = expξ2(xi[:,end-1],1)*expξ2(xi[:,end],1)`
