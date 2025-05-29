```
init_ls!(m::WSVarLmmModel; gniters::Integer = 5)
```

Initialize parameters of a `WSVarLmmModel` object from least squares estimate.  `m.β`  is initialized to be `inv(sum(xi'xi)) * sum(xi'yi)`.  `m.Σγ` is initialized to be `inv(sum(zi'zi⊗zi'zi)) * sum(zi'ri⊗zi'ri)`.   `m.τ`  is initialized to be `inv(sum(wi'wi)) * sum(wi'log(abs2(ri)))`.   If `gniters > 0`, run `gniters` Gauss-Newton iterations to improve τ.
