```
cross_validate_accuracy(X::AbstractMatrix{<:Number},
                        y::AbstractVector{<:Integer};
                        verbose::Bool = true,
                        k::Int = 4,
                        lambda::Real = 1e-5) -> Float64
```

Perform k-fold cross-validation on the dataset `(X, y)` using logistic regression  and return the average classification accuracy.

# Arguments

  * `X::AbstractMatrix`: The feature matrix (observarions x features).
  * `y::AbstractVector{<:Integer}`: The target vector (+-1)
  * `verbose::Bool` (optional): If `true`, prints the accuracy of each fold. Defaults to `true`.
  * `k::Int` (optional): The number of folds for cross-validation. Defaults to 4.
  * `lambda::Real` (optional): Regularization parameter for logistic regression. Defaults to 1e-5.

# Returns

  * `Float64`: The average classification accuracy across all folds.

# Example

```julia
acc = cross_validate_accuracy(Xt, y; k = 4, lambda = 1e-2)
```
