```
r = rtf(num, den; Ts = rts, var = rvar )
```

Create the rational transfer function `r(λ) = num(λ)/den(λ)` with the polynomials `num(λ)` and `den(λ)`,  sampling time `rts` and variable name `rvar`, representing  the transfer function of a single-input single-output system of the form

```
Y(λ) = r(λ) U(λ),
```

where `U(λ)` and `Y(λ)` are the Laplace or `Z` transformed input `u(t)` and output `y(t)`, respectively,  and `λ = s`, the complex variable in the Laplace transform, if `rts = 0`, or  `λ = z`,   the complex variable in the `Z` transform, if `rts ≠ 0`.  Both `num` and `den` can be real or complex numbers as well. 

The resulting `r` is such that `r.Ts = rts` (default `rts = 0`) and `r.var = rvar`. The default value of `rvar` is `rvar = Polynomials.indeterminate(num)` if `num` is a polynomial,  `rvar = Polynomials.indeterminate(den)` if `num` is a number and `den` is a polynomial, and `rvar = :s` if both `num` and `den` are numbers.
