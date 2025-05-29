```julia
HookStiffnessOperator3D(
    μ,
    λ;
    name,
    AT,
    regions,
    ϵ,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

constructor for a bilinearform a(u,v) = (C ϵ(u), ϵ(v)) where C is the 3D stiffness tensor for isotropic media in Voigt notation, i.e. ℂ ϵ(u) = 2 μ ϵ(u) + λ tr(ϵ(u)) for Lame parameters μ and λ

```
In Voigt notation ℂ is a 6 x 6 matrix
ℂ = [c11,c12,c12,  0,  0,  0
     c12,c11,c12,  0,  0,  0
     c12,c12,c11,  0,  0,  0
       0,  0,  0,c44,  0,  0
       0,  0,  0,  0,c44,  0
       0,  0,  0,  0,  0,c44]   

where c44 = μ, c12 = λ and c11 = 2*c44 + c12
```

Note: ϵ is the symmetric part of the gradient (in Voigt notation)
