```
predict_point!(predictions, i, source_values, u, w, dists, dim)
```

The prediction part of the convergent cross mapping algorithm.

## Algorithm

Consider the point in the delay embedding of `target` point with time index `i`. Denote the time indices of its nearest neighbors $t_1, t_2, \ldots, t_{dim+1}$. Denote the scalar values of `source` at those time indices $y_1, y_2, \ldots, y_{dim+1}$.

Given `distances` $d_1, d_2, \ldots, d_{dim+1}$ from the `i`-th point to its nearest neighbors, we compute the weights `w` from the cross mapping algorithm ([Sugihara et al, 2012; supplementary material, page 4](http://science.sciencemag.org/content/sci/suppl/2012/09/19/science.1227079.DC1/Sugihara.SM.pdf)). The weights `w` and coefficients `u` are stored in pre-allocated vectors.

A prediction for the observation with time index `i` in the `source` timeseries, call it $\hat{y}(i)$, is computed as the sum

$$
\hat{y}(i) = \sum_{j=1}^{dim+1} w_j y_j.
$$

We store the prediction $\hat{y}(i)$ in position `i` of the pre-allocated vector `predictions`.

## Arguments

  * **`predictions`**: A pre-allocated vector in which to store the   prediction for the scalar value of the `source` series.
  * **`i`**: The time index of the point of the `source` series being   predicted. The prediction is stored in `predictions[i]`.
  * **`source_values`**: Let $t_1, t_2, \ldots, t_{dim + 1}$ be   the time indices of   the nearest neighbors to the delay embedding point with time   index `i`. `source_values` contains the scalar values of the   `source` series at those time indices.
  * **`u`**: A pre-allocated vector of length `dim + 1` that holds the   normalisation coefficients for computing the weights in the   cross mapping algorithm.
  * **`w`**: A pre-allocated vector of length `dim + 1` that holds   the computed weights for the cross mapping algorithm.
  * **`dists`**: The distances from delay embedding point with time index   `i` to its `dim + 1` nearest neighbors, in order of increasing   distances.
  * **`dim`**: The dimension of the delay embedding.

## References

Sugihara, George, et al. "Detecting causality in complex ecosystems." Science (2012): 1227079. [http://science.sciencemag.org/content/early/2012/09/19/science.1227079](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)
