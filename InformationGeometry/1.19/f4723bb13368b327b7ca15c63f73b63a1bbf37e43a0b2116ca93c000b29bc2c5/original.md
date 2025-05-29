```
VariancePropagation(DM::AbstractDataModel, mle::AbstractVector, Confnum::Real; dof::Int=DOF(DM), kwargs...)
VariancePropagation(DM::AbstractDataModel, mle::AbstractVector, C::AbstractMatrix=quantile(Chisq(length(mle)), ConfVol(1)) * Symmetric(pinv(FisherMetric(DM, mle))); kwargs...)
```

Computes the forward propagation of the parameter covariance to the residuals. The output constitutes the cholesky decomposition (i.e. square root) of the variance associated with the residuals. Matrix `C` corresponds to a parameter covariance matrix `Σ` which has been properly scaled according to a desired confidence level.
