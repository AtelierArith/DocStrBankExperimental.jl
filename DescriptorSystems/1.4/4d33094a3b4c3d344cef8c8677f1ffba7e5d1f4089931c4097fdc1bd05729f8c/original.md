```
timeresp(sys, u, t, x0 = 0; interpolation = "zoh", state_history = false, 
         fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (y, tout, x)
```

Compute the time response of a proper descriptor system `sys = (A-λE,B,C,D)` to the input signals  described by `u` and `t`. The time vector `t` consists of regularly spaced time samples. The  matrix `u` has as many columns as the inputs of `sys` and its `i`-th row specifies  the input values at time `t[i]`. For discrete-time models, `u` should be sampled at the same rate as `sys` if `sys.Ts > 0` and `t` must have all time steps equal to `sys.Ts` or can be set to an empty vector.  The vector `x0` specifies the initial state vector at time `t[1]` and is set to zero when omitted. 

The matrix `y` contains the resulting time history of the outputs of `sys` and  the vector `tout` contains the corresponding values of the time samples. The `i`-th row of `y` contains the output values at time `tout[i]`.   If the keyword parameter value `state_history = false` is used, then the matrix `x` contains  the resulting time history of the state vector and its `i`-th row contains  the state values at time `tout[i]`. By default, the state history is not computed and `x = nothing`.

For continuous-time models, the input values are interpolated between samples. By default,  zero-order hold based interpolation is used. The linear interpolation method can be selected using  the keyword parameter `interpolation = "foh"`.

By default, the uncontrollable infinite eigenvalues and simple infinite eigenvalues of the pair `(A,E)`  are eliminated.  The underlying pencil manipulation algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true` (default), or the SVD-decomposition, if `fast = false`. The rank decision based on the SVD-decomposition is generally more reliable,  but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
