```
expectation_value(peps::InfinitePEPS, O::LocalOperator, env::CTMRGEnv)
```

Compute the expectation value ⟨peps|O|peps⟩ / ⟨peps|peps⟩ of a [`LocalOperator`](@ref) `O` for a PEPS `peps` using a given CTMRG environment `env`.
