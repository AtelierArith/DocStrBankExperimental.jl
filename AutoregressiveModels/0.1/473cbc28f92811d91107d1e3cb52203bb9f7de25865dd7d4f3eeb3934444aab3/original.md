```
residvcov(r::VectorAutoregression, id1, id2=id1)
```

Return the variance-covariance estimate between the reduced-form errors from equation `id1` and `id2`. The equations are indexed by the outcome variables, which can be variable names of type `Symbol` or integer indices.
