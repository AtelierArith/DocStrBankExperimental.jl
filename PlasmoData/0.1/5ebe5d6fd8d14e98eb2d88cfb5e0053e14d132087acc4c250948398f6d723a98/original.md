```
mvts_to_graph(mvts, attribute)
```

Converts a multivariate time series to a graph based on the covariance matrix. This first calculates the covariance of the multivariate time series (`mvts`) and then computes the covariance. It then forms the precision matrix by taking the inverse of the covariance and uses the function `symmetric_matrix_to_graph` to form the edge-weighted graph.
