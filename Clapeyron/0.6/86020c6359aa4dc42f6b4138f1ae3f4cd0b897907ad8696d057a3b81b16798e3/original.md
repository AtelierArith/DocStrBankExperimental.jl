```
COSMOSACdsp(components;
puremodel = PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters:

  * `Pnhb` :Single Parameter{String}
  * `POH` :Single Parameter{String}
  * `POT` :Single Parameter{String}
  * `V`: Single Parameter{Float64}
  * `A`: Single Parameter{Float64}
  * `epsilon`: Single Parameter{Float64}
  * `COOH`: Single Parameter{Float64}
  * `water`: Single Parameter{Float64}
  * `hb_acc`: Single Parameter{Float64}
  * `hb_don`: Single Parameter{Float64}

## Description

An activity coefficient model using molecular solvation based on the COSMO-RS method. Sigma profiles are now split by non-hydrogen bonding, hydrogen acceptor and hydrogen donor. A dispersive correction is included.

## References

1. Klamt, A. (1995). Conductor-like screening model for real solvents: A new approach to the quantitative calculation of solvation phenomena. Journal of Physical Chemistry, 99(7), 2224–2235. [doi:10.1021/j100007a062](https://doi.org/10.1021/j100007a062)
2. Lin, S-T. & Sandler, S.I. (2002). A priori phase equilibrium prediction from a segment contribution solvation model. Industrial & Engineering Chemistry Research, 41(5), 899–913. [doi:10.1021/ie001047w](https://doi.org/10.1021/ie001047w)
3. Hsieh, C-H., Sandler, S.I., & Lin, S-T. (2010). Improvements of COSMO-SAC for vapor–liquid and liquid–liquid equilibrium predictions. Fluid Phase Equilibria, 297(1), 90-97. [doi:10.1016/j.fluid.2010.06.011](https://doi.org/10.1016/j.fluid.2010.06.011)
4. Hsieh, C-H., Lin, S-T. & Vrabec, J. (2014). Considering the dispersive interactions in the COSMO-SAC model for more accurate predictions of fluid phase behavior. Fluid Phase Equilibria, 367, 109-116. [doi:10.1016/j.fluid.2014.01.032](https://doi.org/10.1016/j.fluid.2014.01.032)
