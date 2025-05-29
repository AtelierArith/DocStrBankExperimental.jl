```
solution_approximation(certificate::AbstractSolutionCertificate)
```

`is_certified(certificate)`が`true`の場合、これは与えられた`certificate`の[`certified_solution_interval`](@ref)の中点を`Vector{ComplexF64}`として返します。`is_certified(certificate)`が`false`の場合は`nothing`を返します。
