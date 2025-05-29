```julia
exportG2o(
    dfg;
    poseRegex,
    solvable,
    ignorePriors,
    filename,
    overwriteMapping,
    varIntLabel,
    solveKey
)

```

Export a factor graph to g2o file format.

Note:

  * This funtion only supports Gaussian (i.e. Normal/MvNormal) factors, unpredictable witchcraft is used in other cases such as `AliasingScalarSampler` factor models.
