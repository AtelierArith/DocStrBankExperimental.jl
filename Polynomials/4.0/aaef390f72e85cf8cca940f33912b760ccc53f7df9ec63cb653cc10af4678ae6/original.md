```
AbstractPolynomial{T,X}
```

An abstract type for various polynomials with an *implicit* basis.

A polynomial type holds an indeterminate `X`; coefficients of type `T`, stored in some container type; and an implicit basis, such as the standard basis.

# Properties

  * `coeffs` - The coefficients of the polynomial

# The type `T`

`T` need not be `T <: Number`, at the moment it is not restricted

Some `T`s will not be successful

  * scalar mult: `c::Number * p::Polynomial` should be defined
  * scalar mult: `c::T * p::Polynomial{T}` An  ambiguity when `T <: AbstractPolynomial`
  * scalar mult: `p::Polynomial{T} * c::T` need not commute
  * add/sub: `p::Polynomial{T} + q::Polynomial{T}` should be defined
  * sub: `p -p` sometimes needs `zero{T}` defined
  * poly mult: `p::Polynomial{T} * q::Polynomial{T}` Needs "`T * T`" defined (e.g. `Base.promote_op(*, Vector{Int}, Vector{Int}))` needs to be something.)
  * poly powers: `p::Polynomial{T}^2` needs "`T^2`" defined
  * implicit promotion: `p::Polynomial{T} + c::Number`  needs `convert(T, c)` defined
  * implicit promotion: `p::Polynomial{T} + c::T`  ambiguity if `T <: AbstractPolynomial`
  * evaluation: `p::Polynomial{T}(s::Number)`
  * evaluation `p::Polynomial{T}(c::T)`   needs `T*T` defined
  * evaluation of a `0` polynomial requires `zero(T)` to be defined.
  * derivatives: `derivative(p::Polynomial{T})`
  * integrals: `integrate(p::Polynomial{T})`
