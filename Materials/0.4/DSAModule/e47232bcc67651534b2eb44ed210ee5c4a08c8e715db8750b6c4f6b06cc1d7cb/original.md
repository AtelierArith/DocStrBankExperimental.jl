```
integrate_material!(material::GenericDSA{T}) where T <: Real
```

Material model with dynamic strain aging (DSA). This is similar to the Chaboche material with two backstresses, with both kinematic and isotropic hardening, but this model also features static recovery terms.

This model captures dynamic (and static) strain aging (DSA) induced hardening. The related phenomena are:

  * Portevin le Chatelier effect. Serrated yield, plastic instabilities.
  * Discontinuous yielding
  * Inverse strain rate sensitivity (inverse SRS)
  * Secondary hardening in low cycle fatigue (LCF) tests

These typically occur in a certain temperature/strain rate regime, where the dislocations are pinned due to the diffusion of solute atoms. In the most effective conditions, the speed of diffusion is comparable to the applied strain rate (speed of dislocations).

See:

```
J.-L. Chaboche, A. Gaubert, P. Kanouté, A. Longuet, F. Azzouz, M. Mazière.
Viscoplastic constitutive equations of combustion chamber materials including
cyclic hardening and dynamic strain aging. International Journal of Plasticity
46 (2013), 1--22. http://dx.doi.org/10.1016/j.ijplas.2012.09.011
```

Further reading:

```
M. Mazière, H. Dierke. Investigations on the Portevin Le Chatelier critical
strain in an aluminum alloy. Computational Materials Science 52(1) (2012),
68--72. https://doi.org/10.1016/j.commatsci.2011.05.039
```
