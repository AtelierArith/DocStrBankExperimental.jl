```
quintic_blend(fx::Tuple, xt::Tuple, x, delta_x)
```

Smoothly transitions the results of the functions in `fx` using quintic polynomials, with the transition between the functions at the locations in `xt`. `delta_x` is the half width of the smoothing interval.  The resulting function is C2 continuous
