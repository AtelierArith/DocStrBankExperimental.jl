```
certified_solution_interval(certificate::AbstractSolutionCertificate)
```

Returns an `Arblib.AcbMatrix` representing a vector of complex intervals where a unique zero of the system is contained in. Returns `nothing` if `is_certified(certificate)` is `false`.
