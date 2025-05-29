```
crossmap(source, target;
    dim::Int = 3,
    τ::Int = 1,
    libsize::Int = 10,
    replace::Bool = false,
    n_reps::Int = 100,
    theiler_window::Int = 0,
    tree_type = NearestNeighbors.KDTree,
    distance_metric = Distances.Euclidean(),
    correspondence_measure = StatsBase.cor,
    η::Int = 0)
```

## Algorithm

Compute the cross mapping between a `source` series and a `target` series.

## Arguments

  * **`source`**: The data series representing the putative source process.
  * **`target`**: The data series representing the putative target process.
  * **`dim`**: The dimension of the state space reconstruction (delay embedding)   constructed from the `target` series. Default is `dim = 3`.
  * **`τ`**: The embedding lag for the delay embedding constructed from `target`.   Default is `τ = 1`.
  * **`η`**: The prediction lag to use when predicting scalar values of `source`   fromthe delay embedding of `target`.   `η > 0` are forward lags (causal; `source`'s past influences `target`'s future),   and `η < 0` are backwards lags (non-causal; `source`'s' future influences   `target`'s past). Adjust the prediction lag if you   want to performed lagged ccm   [(Ye et al., 2015)](https://www.nature.com/articles/srep14750).   Default is `η = 0`, as in   [Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079).   *Note: The sign of the lag `η` is organized to conform with the conventions in   [TransferEntropy.jl](), and is opposite to the convention used in the   [`rEDM`](https://cran.r-project.org/web/packages/rEDM/index.html) package   ([Ye et al., 2016](https://cran.r-project.org/web/packages/rEDM/index.html)).*
  * **`libsize`**: Among how many delay embedding points should we sample time indices   and look for nearest neighbours at each cross mapping realization (of which there   are `n_reps`)?
  * **`n_reps`**: The number of times we draw a library of `libsize` points from the   delay embedding of `target` and try to predict `source` values. Equivalently,   how many times do we cross map for this value of `libsize`?   Default is `n_reps = 100`.
  * **`replace`**: Sample delay embedding points with replacement? Default is `replace = true`.
  * **`theiler_window`**: How many temporal neighbors of the delay embedding   point `target_embedding(t)` to exclude when searching for neighbors to   determine weights for predicting the scalar point `source(t + η)`.   Default is `theiler_window = 0`.
  * **`tree_type`**: The type of tree to build when looking for nearest neighbors.   Must be a tree type from NearestNeighbors.jl. For now, this is either   `BruteTree`, `KDTree` or `BallTree`.
  * **`distance_metric`**: An instance of a `Metric` from Distances.jl. `BallTree` and `BruteTree` work with any `Metric`.   `KDTree` only works with the axis aligned metrics `Euclidean`, `Chebyshev`,   `Minkowski` and `Cityblock`. Default is `metric = Euclidean()` *(note the instantiation of the metric)*.
  * **`correspondence_measure`**: The function that computes the correspondence   between actual values of `source` and predicted values. Can be any   function returning a similarity measure between two vectors of values.   Default is `correspondence_measure = StatsBase.cor`, which returns values on $[-1, 1]$.   In this case, any negative values are usually filtered out (interpreted as zero coupling) and   a value of $1$ means perfect prediction.   [Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)   also proposes to use the root mean square deviation, for which a value of $0$ would   be perfect prediction.

## References

Sugihara, George, et al. "Detecting causality in complex ecosystems." Science (2012): 1227079. [http://science.sciencemag.org/content/early/2012/09/19/science.1227079](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)

Ye, Hao, et al. "Distinguishing time-delayed causal interactions using convergent cross mapping." Scientific Reports 5 (2015): 14750. [https://www.nature.com/articles/srep14750](https://www.nature.com/articles/srep14750)

Ye, H., et al. "rEDM: Applications of empirical dynamic modeling from time series." R Package Version 0.4 7 (2016). [https://cran.r-project.org/web/packages/rEDM/index.html](https://cran.r-project.org/web/packages/rEDM/index.html)
