```
certified_solution_interval_after_krawczyk(certificate::ExtendedSolutionCertificate)
```

Returns an `Arblib.AcbMatrix` representing a vector of complex intervals where a unique zero of the system is contained in. This is the result of applying the Krawczyk operator to `certified_solution_interval(certificate)`. Returns `nothing` if `is_certified(certificate)` is `false`.
