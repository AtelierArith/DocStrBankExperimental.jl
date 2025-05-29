```
extract_separable_terms(func::JuMP.AbstractJuMPScalar,graph::OptiGraph)
```

`graph` に含まれる分離可能な項を抽出します。注意: 非線形目的は完全にテストされておらず、誤った結果を返す可能性があります。
