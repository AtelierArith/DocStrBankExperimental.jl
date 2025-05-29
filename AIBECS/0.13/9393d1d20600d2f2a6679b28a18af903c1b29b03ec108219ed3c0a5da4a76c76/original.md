```
λ2p(T::Type{AbstractParameters}, λ::Vector)
```

Converts real-valued vector `λ` back to parameters object `p`.

Note that the instance of your parameters type `T` is required here because it contains information on non-optimizable parameters and priors of optimizable parameters
