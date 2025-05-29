```
pidc = PIDController(Kc, τI, τD, α=0.0)
```

Construct a Proportional-Integral-Derivative (PID) controller by specifying the controller gain, integral time constant, derivative time constant, and derivative filter defined under the following transfer function representation:

$$
g_c(s)=K_c \left[1+\frac{1}{\tau_I s}+\tau_D s \frac{1}{\alpha \tau_D s + 1}\right]
$$

# Arguments

  * `Kc::Float64`: controller gain
  * `τI::Float64`: integral time constant
  * `τD::Float64`: derivative time constant
  * `α::Float64`: derivative filter

# Example

```julia
pidc = PIDController(1.0, 3.0, 0.1) # specify PID controller params
gc = TransferFunction(pidc) # construct transfer function with these PID-controller params
```
