```
zpk(gain[, Ts])
zpk(num, den, k[, Ts])
zpk(sys)
```

Create transfer function on zero pole gain form. The numerator and denominator are represented by their poles and zeros.

  * `sys::TransferFunction{SisoZpk{T,TR}} = k*numerator/denominator`

where `T` is the type of `k` and `TR` the type of the zeros/poles, usually Float64 and Complex{Float64}.

  * `num`: the roots of the numerator polynomial. Either scalar or vector to create SISO systems

or an array of vectors to create MIMO system.

  * `den`: the roots of the denominator polynomial. Either vector to create SISO systems

or an array of vectors to create MIMO system.

  * `k`: The gain of the system. Obs, this is not the same as `dcgain`.
  * `Ts`: Sample time if discrete time system.

Other uses:

  * `zpk(sys)`: Convert `sys` to `zpk` form.
  * `zpk("s")`: Create the transferfunction `s`.
