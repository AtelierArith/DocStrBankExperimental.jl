```
integrate_material!(material::GenericChaboche{T}) where T <: Real
```

Chaboche material with two backstresses. Both kinematic and isotropic hardening.

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
