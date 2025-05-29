A struct detailing an ito integral. It contains a UnivariateFunction detailing the integrand as well as a symbol detailing an id of the integral's processes.

Usual (and most general) contructor is:

```
ItoIntegral(brownian_id_::Symbol, f_::UnivariateFunction)
```

Convenience constructor for `ItoIntegral`s where the integrand is a flat function is:

```
ItoIntegral(brownian_id_::Symbol, variance_::Real)
```
