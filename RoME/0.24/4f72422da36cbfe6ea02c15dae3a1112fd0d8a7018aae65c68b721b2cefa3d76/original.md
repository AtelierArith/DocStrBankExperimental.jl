```julia
duplicateToStandardFactorVariable(
    ,
    mpp,
    dfg,
    prevsym,
    newsym;
    solvable,
    graphinit,
    cov
)

```

Helper function to duplicate values from a special factor variable into standard factor and variable.  Returns the name of the new factor.

Notes:

  * Developed for accumulating odometry in a `MutablePosePose` and then cloning out a standard PosePose and new variable.
  * Does not change the original MutablePosePose source factor or variable in any way.
  * Assumes timestampe from mpp object.

Related

[`addVariable!`](@ref), [`addFactor!`](@ref)
