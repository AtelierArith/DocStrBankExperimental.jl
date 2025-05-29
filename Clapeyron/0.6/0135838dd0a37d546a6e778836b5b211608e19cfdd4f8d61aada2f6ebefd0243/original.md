```
ZeroResidual <: EoSModel
ZeroResidual(components; 
idealmodel = BasicIdeal,
ideal_userlocations = String[],
verbose = false)
```

## Input parameters

None

## Description

Zero residual model.

```
    a_res(model,V,T,z) = 0
```
