```julia
HookStiffnessOperator2D(
    μ,
    λ;
    name,
    AT,
    regions,
    ϵ,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

constructor for a bilinearform a(u,v) = (C ϵ(u), ϵ(v)) where C is the 2D stiffness tensor for isotropic media in Voigt notation, i.e. ℂ ϵ(u) = 2 μ ϵ(u) + λ tr(ϵ(u)) for Lame parameters μ and λ

```
In Voigt notation ℂ is a 3 x 3 matrix
ℂ = [c11,c12,  0
     c12,c11,  0
       0,  0,c33]

where c33 = μ, c12 = λ and c11 = 2*c33 + c12
```

Note: ϵ is the symmetric part of the gradient (in Voigt notation)
