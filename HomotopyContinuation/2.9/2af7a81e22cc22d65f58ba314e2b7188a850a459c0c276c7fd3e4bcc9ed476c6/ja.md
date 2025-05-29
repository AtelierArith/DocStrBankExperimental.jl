```
certified_solution_interval_after_krawczyk(certificate::ExtendedSolutionCertificate)
```

`Arblib.AcbMatrix`を返し、システムの一意のゼロが含まれている複素数区間のベクトルを表します。これは、`certified_solution_interval(certificate)`にKrawczyk演算子を適用した結果です。`is_certified(certificate)`が`false`の場合は`nothing`を返します。
