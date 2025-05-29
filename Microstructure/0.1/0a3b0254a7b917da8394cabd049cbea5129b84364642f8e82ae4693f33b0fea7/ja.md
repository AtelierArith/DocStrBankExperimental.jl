```
MTE_SANDI(
    soma::Sphere 
    neurite::Stick
    extra::Iso 
    fracs::Vector{Float64} 
    )
```

Multi-echo-SANDI (MTE-SANDI)モデルでは、すべてのコンパートメントにおける`t2`値を考慮し、推定される分数は上記のモデルと比較して非T2加重コンパートメント分数になります。

# 参考文献

Gong, T., Tax, C.M., Mancini, M., Jones, D.K., Zhang, H., Palombo, M., 2023. Multi-TE SANDI: Quantifying compartmental T2 relaxation times in the grey matter. Toronto.
