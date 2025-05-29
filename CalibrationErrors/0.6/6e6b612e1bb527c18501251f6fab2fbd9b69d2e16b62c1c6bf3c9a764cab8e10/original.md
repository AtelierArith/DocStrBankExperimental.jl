```
ECE(binning[, distance = TotalVariation()])
```

Estimator of the expected calibration error (ECE) for a classification model with respect to the given `distance` function using the `binning` algorithm.

For classification models, the predictions $P_{X_i}$ and targets $Y_i$ are identified with vectors in the probability simplex. The estimator of the ECE is defined as

$$
\frac{1}{B} \sum_{i=1}^B d\big(\overline{P}_i, \overline{Y}_i\big),
$$

where $B$ is the number of non-empty bins, $d$ is the distance function, and $\overline{P}_i$ and $\overline{Y}_i$ are the average vector of the predictions and the average vector of targets in the $i$th bin. By default, the total variation distance is used.

The `distance` has to be a function of the form

```julia
distance(pbar::Vector{<:Real}, ybar::Vector{<:Real}).
```

In particular, distance measures of the package [Distances.jl](https://github.com/JuliaStats/Distances.jl) are supported.
