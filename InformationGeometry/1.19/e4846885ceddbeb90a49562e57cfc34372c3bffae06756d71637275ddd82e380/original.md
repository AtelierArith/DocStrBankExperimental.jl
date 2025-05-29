```
MLEuncert(DM::AbstractDataModel, mle::AbstractVector=MLE(DM), F::AbstractMatrix=FisherMetric(DM, mle))
```

Returns vector of type `Measurements.Measurement` where the parameter uncertainties are approximated via the diagonal of the inverse Fisher metric. That is, the stated uncertainties are a linearized symmetric approximation of the true parameter uncertainties around the MLE.
