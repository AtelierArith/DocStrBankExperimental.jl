```
pic = PIController(Kc, τI)
```

Construct a Proportional-Integral (PI) controller by specifying the controller gain and integral time constant defined under the following transfer function representation:

$$
g_c(s)=K_c \left[1+\frac{1}{\tau_I s}\right]
$$

# Arguments

  * `Kc::Float64`: controller gain
  * `τI::Float64`: integral time constant

# Example

```julia
pic = PIController(1.0, 3.0) # specify PI controller params
gc = TransferFunction(pic) # construct transfer function with these PI-controller params
```
