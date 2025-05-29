```
function LinearElasticityProblem(
    dimension::Int = 2;
    elasticity_modulus = 1.0,
    shear_modulus = 1.0,
    lambda = 1.0)
```

Creates a PDEDescription for the linear elasticity problem of the specified dimension.

If dimension == 1, only the elasticity*modulus is used as a parameter in the Hookian stiffness operator. If dimension == 2, shear*modulus and lambda are used as Lame parameters in the Hookian stiffness operator.

Boundary and right-hand side data or other modifications have to be added afterwards.
