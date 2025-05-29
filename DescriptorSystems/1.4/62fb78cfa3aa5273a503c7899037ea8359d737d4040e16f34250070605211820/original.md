```
Rd = c2d(Rc, Ts, meth = "zoh"; prewarp_freq = freq, atol = 0, rtol = n*ϵ)
```

Compute for the continuous-time rational transfer function matrix `Rc` and for a sampling time `Ts`,  the corresponding discretized rational transfer function matrix `Rd`    according to the selected discretization method specified by `meth`. 

The following discretization methods can be performed by appropriately selecting `meth`:

```
  "zoh"     - zero-order hold on the inputs (default); 

  "foh"     - linear interpolation of inputs (also known as first-order hold);

  "impulse" - impulse-invariant discretization; 
  
  "matched" - matched pole-zero method (see [1]); 
  
  "Tustin"  - Tustin transformation (also known as trapezoidal integration): a nonzero prewarping frequency
              `freq` can be specified using the keyword parameter `prewarp_freq = freq` to ensure 
              `Rd(exp(im*freq*Ts)) = Rc(im*freq)`.
```

The keyword arguments `atol` and `rtol` specify, respectively,  the absolute and relative tolerances, respectively,  for the nonzero coefficients of the numerator and denominator polynomials of the elements of `Rc`.   The default relative tolerance is `10*ϵ`, where `ϵ` is the working machine epsilon. 

*References*:

[1] G.F. Franklin, D.J. Powell and  M.L. Workman, Digital Control of Dynamic Systems (3rd Edition), Prentice Hall, 1997.
