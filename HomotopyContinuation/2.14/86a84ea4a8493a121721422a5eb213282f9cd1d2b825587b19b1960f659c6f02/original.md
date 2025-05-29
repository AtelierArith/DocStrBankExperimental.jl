```
is_positive(certificate::AbstractSolutionCertificate, i)
```

Returns `true` if `is_certified(certificate)` is `true` and `i`-th coordinate of the unique zero contained in `certified_solution_interval(certificate)` is real and positive.
