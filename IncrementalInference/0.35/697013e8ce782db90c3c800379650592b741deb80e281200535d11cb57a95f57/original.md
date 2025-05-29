```julia
addFactor!(
    dfg,
    Xi,
    usrfnc;
    multihypo,
    nullhypo,
    solvable,
    tags,
    timestamp,
    graphinit,
    suppressChecks,
    inflation,
    namestring,
    _blockRecursion
)

```

Add factor with user defined type `<:AbstractFactor``to the factor graph object. Define whether the automatic initialization of variables should be performed.  Use order sensitive`multihypo` keyword argument to define if any variables are related to data association uncertainty.

Experimental

  * `inflation`, to better disperse kernels before convolution solve, see IIF #1051.
