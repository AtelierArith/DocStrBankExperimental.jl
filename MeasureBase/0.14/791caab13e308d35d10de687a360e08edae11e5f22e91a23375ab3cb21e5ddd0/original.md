```
smf(μ, x::Real) ::Real
```

Compute the *Stieltjes measure function (SMF)* of the measure `μ` at the point `x`.

The SMF is the measure-theoretic generalization of the *cumulative distribution function (CDF)* from probability theory. An SMF `F(x) = smf(μ, x)` must have the following properties:

1. F is *nondecreasing*
2. F is *right-continuous*: `F(x)` should be the same as `lim_{δ→0} F(x + |δ|)`.
3. μ((a,b]) = F(b) - F(a)

Note that unlike the CDF, an SMF is only determined up to addition by a constant. For many applications, this leads to a need to evaluate an SMF at -∞. It's therefore important that `smf(μ, -Inf)` be fast. In practice, this will usually be called as `smf(μ, static(-Inf))`. It's then easy to ensure speed and avoid complex control flow by adding a method `smf(μ::M, ::StaticFloat64{-Inf})`.

Users who pronounce `sinh` as "sinch" are advised to pronounce `smf` as "smurf".
