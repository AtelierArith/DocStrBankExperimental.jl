```
sys = tf(num, den[, Ts])
sys = tf(gain[, Ts])
```

Create as a fraction of polynomials:

  * `sys::TransferFunction{SisoRational{T,TR}} = numerator/denominator`

where T is the type of the coefficients in the polynomial.

  * `num`: the coefficients of the numerator polynomial. Either scalar or vector to create SISO systems

or an array of vectors to create MIMO system.

  * `den`: the coefficients of the denominator polynomial. Either vector to create SISO systems

or an array of vectors to create MIMO system.

  * `Ts`: Sample time if discrete time system.

The polynomial coefficients are ordered starting from the highest order term. 

Other uses:

  * `tf(sys)`: Convert `sys` to `tf` form.
  * `tf("s")`, `tf("z")`: Create the continuous-time transfer function `s`, or the discrete-time transfer function `z`.
  * `numpoly(sys)`, `denpoly(sys)`: Get the numerator and denominator polynomials of `sys` as a matrix of vectors, where the outer matrix is of size `n_output × n_inputs`.

See also: [`zpk`](@ref), [`ss`](@ref).
