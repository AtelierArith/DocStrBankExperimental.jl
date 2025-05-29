```
integrate_material!(material::GenericMemory{T}) where T <: Real
```

Material model with a strain memory effect.

This is similar to the Chaboche material with two backstresses, with both kinematic and isotropic hardening, but this model also features a strain memory term.

Strain memory is used to be able to model strain amplitude-dependent isotropic hardening. In practice, the transition from a tensile test curve to cyclic behavior can be captured with this model.

See:

```
D. Nouailhas, J.-L. Chaboche, S. Savalle, G. Cailletaud. On the constitutive
equations for cyclic plasticity under nonproportional loading. International
Journal of Plasticity 1(4) (1985), 317--330.
https://doi.org/10.1016/0749-6419(85)90018-X
```
