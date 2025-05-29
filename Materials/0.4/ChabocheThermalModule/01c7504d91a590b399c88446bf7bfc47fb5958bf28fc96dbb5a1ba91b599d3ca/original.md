```
integrate_material!(material::GenericChabocheThermal{T}) where T <: Real
```

Chaboche viscoplastic material with thermal effects. The model includes kinematic hardening with three backstresses, and isotropic hardening.

Let the prime (') denote the time derivative. The evolution equations are:

σ' = D : εel' + dD/dθ : εel θ'   R' = b (Q - R) p'   Xj' = ((2/3) Cj n - Dj Xj) p'   (no sum)

where j = 1, 2, 3. The strain consists of elastic, thermal and viscoplastic contributions:

ε = εel + εth + εpl

Outside the elastic region, the viscoplastic strain response is given by:

εpl' = n p'

where

n = ∂f/∂σ

and p' obeys a Norton-Bailey power law:

p' = 1/tvp * (<f> / Kn)^nn

Here <...> are the Macaulay brackets (a.k.a. positive part), and the yield criterion is of the von Mises type:

f = √(3/2 dev(σ*eff) : dev(σ*eff)) - (R0 + R)   σ_eff = σ - ∑ Xj

See:

```
J.-L. Chaboche. Constitutive equations for cyclic plasticity and cyclic
viscoplasticity. International Journal of Plasticity 5(3) (1989), 247--302.
https://doi.org/10.1016/0749-6419(89)90015-6
```

Further reading:

```
J.-L. Chaboche. A review of some plasticity and viscoplasticity constitutive
theories. International Journal of Plasticity 24 (2008), 1642--1693.
https://dx.doi.org/10.1016/j.ijplas.2008.03.009

J.-L. Chaboche, A. Gaubert, P. Kanouté, A. Longuet, F. Azzouz, M. Mazière.
Viscoplastic constitutive equations of combustion chamber materials including
cyclic hardening and dynamic strain aging. International Journal of Plasticity
46 (2013), 1--22. https://dx.doi.org/10.1016/j.ijplas.2012.09.011
```
