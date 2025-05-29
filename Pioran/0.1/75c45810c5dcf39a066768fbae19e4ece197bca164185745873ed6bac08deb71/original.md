```
Exp(A, α)
```

Exponential covariance Function

  * `A`: the amplitude of the covariance function
  * `α`: the decay rate of the covariance function

$$
k(τ) = A \exp(-α τ)
$$

# Example

```julia
Exp(1.0, 0.25)
```
