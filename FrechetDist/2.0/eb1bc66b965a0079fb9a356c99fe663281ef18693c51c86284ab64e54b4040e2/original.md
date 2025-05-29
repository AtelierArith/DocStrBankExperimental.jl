```
frechet_d_r_compute
```

Compute discrete frechet distance that is locally optimal Frechet. Essentially discrete frechet + Prim/Dijkstra algorithm For the discrete case, that is modified to be retractable – that is minimize the maximum bottleneck edge being computed.

Note, the function still allocates quadratic space for the lookup tables. Doesn't seem to matter, but this might be worth fixing in future versions.
