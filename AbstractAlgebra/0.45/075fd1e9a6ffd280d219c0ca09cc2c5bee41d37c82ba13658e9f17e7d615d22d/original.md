```
fraction_field(R::Ring; cached::Bool=true)
```

Return the parent object of the fraction field over the given base ring $R$. If `cached == true` (the default), the returned parent object is cached so that it will always be returned by a call to the constructor when the same base ring $R$ is supplied.
