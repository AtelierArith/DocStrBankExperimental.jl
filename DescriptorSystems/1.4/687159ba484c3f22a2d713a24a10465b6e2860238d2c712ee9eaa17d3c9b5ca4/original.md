```
r = RationalTransferFunction(num::AbstractPolynomial, den::AbstractPolynomial, Ts:Real)
```

Construct a rational transfer function model `r` from its numerator and denominator polynomials  `num` and `den`, respectively, and sampling time `Ts`. 

If `r::RationalTransferFunction{T,λ,P <: Polynomial(T,λ),Ts}` is a rational transfer function system model  object defined as `r(λ) = num(λ)/den(λ)`, where  `num(λ)` and `den(λ)` are polynomials  with coefficients in `T` and with the indeterminate `λ`, and `Ts` is the sampling time, then:

`r.num` is the numerator polynomial `num(λ)`; 

`r.den` is the denominator polynomial `den(λ)`. 

The sampling time `Ts` can have the following values:

  * `Ts = 0` for a continuous-time system and           `λ = s` is the complex variable in the Laplace transform;
  * `Ts > 0` or `Ts = -1` for a discrete-time system and           `λ = z` is the complex variable in the `Z`-transform;           `Ts = -1` indicates a discrete-time system with an unspecified sampling time.

The sampling time can be obtained as `r.Ts`. The symbol (or *variable*) used for the indeterminate `λ` is the common symbol used for the  indeterminates of the polynomials `num(λ)` and `den(λ)` and can be obtained as `r.var`.  The roots of the numerator polynomial `num(λ)` (also called *zeros* of `r(λ)`) can be obtained as `r.zeros`, while the roots of the denominator polynomial `den(λ)`  (also called *poles* of `r(λ)`) can be obtained as `r.poles`.  The ratio of the leading polynomial coefficients of `num(λ)` and `den(λ)`  (also called *gain* of `r(λ)`) can be obtained as `r.gain`.
