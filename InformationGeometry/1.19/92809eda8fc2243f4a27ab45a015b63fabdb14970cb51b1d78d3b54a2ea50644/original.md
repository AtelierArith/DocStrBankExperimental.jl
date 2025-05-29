```
GeneralizedDOF(DM::AbstractDataModel)
```

Computes the generalized degrees of freedom for a given `DataModel` which can take non-integer values and is defined in: https://doi.org/10.1093/biomet/asv019 https://doi.org/10.2307/2669609 Its definition is based on the fact that the expected prediction error (EPE) is overestimated by the residual squared sum (RSS) by an amount `2σ^2 * dof`. It can be computed as $\sum_{i=1}^{n} \partial \hat{y}_i / \partial {y_\text{data}}_i$.
