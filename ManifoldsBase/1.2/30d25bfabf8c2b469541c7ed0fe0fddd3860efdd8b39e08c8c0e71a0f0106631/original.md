```
StabilizedRetraction <: AbstractRetractionMethod
```

A retraction wraps another retraction and projects the resulting point onto the manifold for numerical stability.

# Constructor

```
StabilizedRetraction(::AbstractRetractionMethod=ExponentialRetraction())
```
