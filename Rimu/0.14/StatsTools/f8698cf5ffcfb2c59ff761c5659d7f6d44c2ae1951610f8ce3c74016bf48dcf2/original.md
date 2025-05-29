```
w_exp(shift, h, time_step; E_r = mean(shift), skip = 0)
```

Compute the weights for reweighting over `h` time steps with reference energy `E_r` from the exponential formula

$$
w_h^{(n)} = \prod_{j=1}^h \exp[-dτ(S^{(q+n-j)}-E_r)] ,
$$

where `q = skip` and $dτ$ is the `time_step`.

See also [`w_lin`](@ref), [`growth_estimator`](@ref), [`mixed_estimator`](@ref).
