```
thermo_Psi!(model::Physics{T,F,M,Tu,E,D,BI}, Psif::FaceScalarField) 
where {T,F<:AbstractCompressible,M,Tu,E,D,BI}
```

Function updates the value of Psi.

### Input

  * `model`  – Physics model defined by user.
  * `Psif`    – Compressibility factor FaceScalarField.

### Algorithm

Weakly compressible currently uses the ideal gas equation for establishing the compressibility factor where $\rho = p * \Psi$. $\Psi$ is calculated from the sensible  enthalpy, reference temperature and fluid model specified $C_p$ and $R$ value where  $R$ is calculated from $C_p$ and $\gamma$ specified in the fluid model.
