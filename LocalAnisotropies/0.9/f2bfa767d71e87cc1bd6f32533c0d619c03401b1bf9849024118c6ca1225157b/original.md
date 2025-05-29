```
graph(domain, localaniso, metric, searcher)
graph(domain, localaniso, metric, refvariogram, searcher)
```

graph(samples, domain, localaniso, metric, searcher)     graph(samples, domain, localaniso, metric, refvariogram, searcher)

Create a graph connecting `domain` and `samples` points locally. Number of edges/neighbors are defined by the `searcher` object associated to the domain. Distance between points are based on local anisotropies `localaniso` and the desired `metric` to calculate distance between two points. Available metrics:

  * `AnisoDistance`   - averaged anisotropic distance
  * `KernelVariogram` - non-stationary variogram kernel estimator

A reference variogram `refvariogram` is necessary if metric is `KernelVariogram`.
