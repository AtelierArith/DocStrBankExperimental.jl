```
StatLossCov(mode::Symbol)
```

Specify a loss function for which the estimated covariance will be optimal. `mode` is one of `:st`, `:ent`, `:div`, `:aff`, or `:fre`, as specified in Table 2 (p. 1757) of Donoho et al. (2018). In the table below, `A` and `B` are the target and sample covariances, respectively:

| `mode` |                                            loss |                                                                          Interpretation |
| ------:| -----------------------------------------------:| ---------------------------------------------------------------------------------------:|
|  `:st` | `st(A, B) = tr(A⁻¹ B - I) - log(det(B)/det(A))` | Minimize KL-divergence between `N(0, A)` and `N(0, B)` where `N` is normal distribution |
| `:ent` |                                      `st(B, A)` |                                                Minimize errors in Mahalanobis distances |
| `:div` |                           `st(A, B) + st(B, A)` |                                                                                         |
| `:aff` |  `0.5 * log(det(A + B) / (2 * sqrt(det(A*B))))` |                             Minimize Hellinger distance between `N(0, A)` and `N(0, B)` |
| `:fre` |                        `tr(A + B - 2sqrt(A*B))` |                                                                                         |
