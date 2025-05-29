```
time_scale(sys::AbstractStateSpace{Continuous}, a; balanced = false)
time_scale(G::TransferFunction{Continuous},     a; balanced = true)
```

Rescale the time axis (change time unit) of `sys`.

For systems where the dominant time constants are very far from 1, e.g., in electronics, rescaling the time axis may be beneficial for numerical performance, in particular for continuous-time simulations.

Scaling of time for a function $f(t)$ with Laplace transform $F(s)$ can be stated as

$$
f(at) \leftrightarrow \dfrac{1}{a} F\big(\dfrac{s}{a}\big)
$$

The keyword argument `balanced` indicates whether or not to apply a balanced scaling on the `B` and `C` matrices. For statespace systems, this defaults to false since it changes the state representation, only `B` will be scaled. For transfer functions, it defaults to true.

# Example:

The following example show how a system with a time constant on the order of one micro-second is rescaled such that the time constant becomes 1, i.e., the time unit is changed from seconds to micro-seconds. 

```julia
Gs  = tf(1, [1e-6, 1])     # micro-second time scale modeled in seconds
Gms = time_scale(Gs, 1e-6) # Change to micro-second time scale
Gms == tf(1, [1, 1])       # Gms now has micro-seconds as time unit
```

The next example illustrates how the time axis of a time-domain simulation changes by time scaling 

```julia
t = 0:0.1:50 # original time axis
a = 10       # Scaling factor
sys1 = ssrand(1,1,5)
res1 = step(sys1, t)      # Perform original simulation
sys2 = time_scale(sys, a) # Scale time
res2 = step(sys2, t ./ a) # Simulate on scaled time axis, note the `1/a`
isapprox(res1.y, res2.y, rtol=1e-3, atol=1e-3)
```
