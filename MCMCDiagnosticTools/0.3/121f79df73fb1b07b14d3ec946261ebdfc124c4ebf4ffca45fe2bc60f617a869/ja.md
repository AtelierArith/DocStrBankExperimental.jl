```
gelmandiag_multivariate(samples::AbstractArray{<:Real,3}; alpha::Real=0.05)
```

`samples`の形状が`(draws, chains, parameters)`のマルチバリアントGelman、Rubin、Brooks診断を計算します。
