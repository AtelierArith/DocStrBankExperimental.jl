```
logclosure_amplitude(model, p1, p2, p3, p4)
```

Computes the log-closure amplitude of model `m` at the uv-quadrangle u1,v1 -> u2,v2 -> u3,v3 -> u4,v4 using the formula

$$
C = \log\left|\frac{V(u1,v1)V(u2,v2)}{V(u3,v3)V(u4,v4)}\right|
$$

If you want to compute log closure amplitudemap over a number of triangles consider using the `logclosure_amplitudemap` function.
