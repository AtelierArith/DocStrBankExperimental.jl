```
MLE(DM::DataModel) -> Vector
```

Returns the parameter configuration $\theta_\text{MLE} \in \mathcal{M}$ which is estimated to have the highest likelihood of producing the observed data (under the assumption that the specified model captures the true relationship present in the data). For performance reasons, the maximum likelihood estimate is stored as a part of the `DataModel` type.
