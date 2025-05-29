```
SFCCInverseEnthalpyObjective{TF,Tkwargs<:NamedTuple,Thc,TL,TH,Tsat} <: AbstractSFCCObjective
```

Optimization objective for finding a temperature, `T`, wich resolves the conservation equation:

$$
0 = (H - Lθ)/C - T
$$

given a fixed enthalpy value `H` and freeze curve arguments `f_args`.
