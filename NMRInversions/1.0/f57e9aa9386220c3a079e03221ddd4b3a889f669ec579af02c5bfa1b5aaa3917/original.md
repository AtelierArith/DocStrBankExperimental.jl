# Inversion for 1D pulse sequences:

```
invert(seq, x, y ; lims, alpha, solver, normalize)
```

This function will build a kernel and use it to perform an inversion using the algorithm of your choice. The output is an `inv_out_1D` structure.

Necessary (positional) arguments:

  * `seq` is the 1D pulse sequence (e.g. IR, CPMG, PFG)
  * `x` is the experiment x axis (time or b factor etc.)
  * `y` is the experiment y axis (intensity of the NMR signal)

Optional (keyword) arguments:

  * `lims=(a,b,c)` will set the "limits" of the output X,

so that it starts from 10^a, ends in 10^b and consists of c  logarithmically spaced values  (default is (-5, 1, 128) for relaxation and (-10, -7, 128) for diffusion).  Alternatively, a vector of values can be used directly, if more freedom is needed  (e.g. `lims=exp10.(range(-4, 1, 128))`).

  * `alpha` determines the smoothing term. Use a real number for a fixed alpha.

No selection will lead to automatically determining alpha through the  default method, which is `gcv()`.

  * `solver` is the algorithm used to do the inversion math. Default is `brd`.
  * `normalize` will normalize `y` to 1 at the max value of `y`. Default is `true`.
