```
PointwiseLearn(model)
```

A learning solver that converts geospatial data to a tabular format with features (and possibly labels) for each point, and then solves the problem with classical statistical learning `model`.

## Parameters

  * `model` - Learning model implementing the `MLJModelInterface.jl`.

## References

  * Hoffimann et al. 2020. [Geostatistical Learning: Challenges and Opportunities](https://arxiv.org/abs/2102.08791)
