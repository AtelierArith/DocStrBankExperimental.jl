```
pc = PController(Kc)
```

Construct a Proportional (P) controller by specifying the controller gain defined under the following transfer function representation:

$$
g_c(s)=K_c
$$

# Arguments

  * `Kc::Float64`: controller gain

# Example

```julia
pc = PController(1.0) # specify P controller gain
gc = TransferFunction(pc) # construct transfer function with this P-controller gain
```
