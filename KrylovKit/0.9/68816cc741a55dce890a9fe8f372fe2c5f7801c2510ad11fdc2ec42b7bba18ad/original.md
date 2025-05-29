```
rayleighextension(fact::KrylovFactorization)
```

Return the vector `b` appearing in the definition of a [`KrylovFactorization`](@ref); often it is simply the last coordinate unit vector, which can be represented using [`SimpleBasisVector`](@ref).
