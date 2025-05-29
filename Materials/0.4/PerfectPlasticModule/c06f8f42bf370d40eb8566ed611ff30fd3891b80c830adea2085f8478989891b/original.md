```
integrate_material!(material::GenericPerfectPlastic)
```

Perfect plastic material: no hardening. The elastic region remains centered on the origin, and retains its original size.

This is a standard basic plasticity model; see a textbook, such as:

```
J. C. Simo, T. J. R. Hughes. Computational Inelasticity. Interdisciplinary
Applied Mathematics volume 7. Springer. 1998. http://dx.doi.org/10.1007/b98904

The notation in the book somewhat differs from ours; see:
https://github.com/JuliaFEM/Materials.jl/pull/66#issuecomment-674786955
```
