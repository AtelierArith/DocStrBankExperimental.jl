```
StatefulJacobianNormalFormOperator(vjp_operator, jvp_operator, cache)
```

これはノーマルフォームヤコビアンオペレーターを構築します。すなわち、これはヤコビアンオペレーター`J`に対応する`JᵀJ`のオペレーターを構築します。これは直接構築することを意図しておらず、2つの[`StatefulJacobianOperator`](@ref)sの`*`で構築されます。
