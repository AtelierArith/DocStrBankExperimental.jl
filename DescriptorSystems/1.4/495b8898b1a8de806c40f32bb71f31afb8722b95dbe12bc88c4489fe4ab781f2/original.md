```
c2d(sysc, Ts, meth = "zoh"; x0, u0, standard = true, fast = true, prewarp_freq = freq, 
           state_mapping = false, simple_infeigs = true, 
           atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysd, xd0, Mx, Mu)
```

Compute for the continuous-time descriptor system `sysc = (A-sE,B,C,D)` with the proper  transfer function matrix `Gc(λ)` and for a sampling time `Ts`, the corresponding discretized descriptor system `sysd = (Ad-zEd,Bd,Cd,Dd)` with the transfer function matrix `Gd(z)`  according to the selected discretization method specified by `meth`.  The keyword argument `standard` specifies the option to compute a standard state-space realization  of `sysd` (i.e., with `Ed = I`), if `standard = true` (default),  or a descriptor system realization if `standard = false`.  The keyword argument `simple_infeigs = true` indicates that only simple infinite eigenvalues  of the pair `(A,E)` are to be expected (default). The setting `simple_infeigs = false` indicates that possible uncontrollable or unobservable  higher order infinite generalized eigenvalues of the pair `(A,E)` are present and have to be removed.  `xd0` is the mapped initial condition of the state of the discrete-time system `sysd` determined from the  initial conditions of the state `x0` and input `u0` of the continuous-time system `sysc`.  The keyword argument `state_mapping = true` specifies the option to compute the state mapping matrices `Mx` and `Mu` such that  the values `xc(t)` and `xd(t)` of the system state vectors of the continuous-time system `sysc` and of the discrete-time system `sysd`, respectively, and of the input vector `u(t)` are related as `xc(t) = Mx*xd(t)+Mu*u(t)`.    If `state_mapping = false` (the default option), then `Mx = nothing` and `Mu = nothing`.

The following discretization methods can be performed by appropriately selecting `meth`:

```
"zoh"     - zero-order hold on the inputs (default); 

"foh"     - linear interpolation of inputs (also known as first-order hold);

"impulse" - impulse-invariant discretization; 

"Tustin"  - Tustin transformation (also known as trapezoidal integration): a nonzero prewarping frequency
            `freq` can be specified using the keyword parameter `prewarp_freq = freq` to ensure 
            `Gd(exp(im*freq*Ts)) = Gc(im*freq)`.
```

The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true` (default), or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable,  but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
