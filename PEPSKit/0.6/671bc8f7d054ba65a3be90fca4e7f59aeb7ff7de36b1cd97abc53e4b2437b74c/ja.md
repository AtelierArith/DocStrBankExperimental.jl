```
expectation_value(peps::InfinitePEPS, O::LocalOperator, env::CTMRGEnv)
```

PEPS `peps` に対して与えられた CTMRG 環境 `env` を使用して、[`LocalOperator`](@ref) `O` の期待値 ⟨peps|O|peps⟩ / ⟨peps|peps⟩ を計算します。
