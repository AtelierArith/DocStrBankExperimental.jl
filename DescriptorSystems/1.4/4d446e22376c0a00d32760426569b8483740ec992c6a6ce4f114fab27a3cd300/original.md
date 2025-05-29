```
rd = c2d(rc, Ts, meth = "zoh"; prewarp_freq = freq, atol = 0, rtol = n*ϵ)
```

Compute for the continuous-time rational transfer function `rc` and for a sampling time `Ts`,  the corresponding discretized rational transfer function `rd`    according to the selected discretization method specified by `meth`. 

The following discretization methods can be performed by appropriately selecting `meth`:

```
"zoh"     - zero-order hold on the inputs (default); 

"foh"     - linear interpolation of inputs (also known as first-order hold);

"impulse" - impulse-invariant discretization; 

"matched" - matched pole-zero method (see [1]); 

"Tustin"  - Tustin transformation (also known as trapezoidal integration): a nonzero prewarping frequency
            `freq` can be specified using the keyword parameter `prewarp_freq = freq` to ensure 
            `rd(exp(im*freq*Ts)) = rc(im*freq)`.
```

The keyword arguments `atol` and `rtol` specify, respectively,  the absolute and relative tolerances, respectively,  for the nonzero coefficients of the numerator and denominator polynomials of  `rc`.   The default relative tolerance is `n*ϵ`, where `n` is the order of `rc`  (i.e., the maximum degree of the numerator and denominator polynomials) and  `ϵ` is the working machine epsilon. 

*References*:

[1] G.F. Franklin, D.J. Powell and  M.L. Workman, Digital Control of Dynamic Systems (3rd Edition), Prentice Hall, 1997.
