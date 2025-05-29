```
chain_complex(A::Map{FinGenAbGroup, FinGenAbGroup, <:Any, <:Any}...) -> ComplexOfMorphisms{FinGenAbGroup}
```

写像 $A_i$ が $\Im(A_i) \subseteq \Kern(A_{i+1})$ を満たす場合、これによりコチェイン複体が作成されます。チェイン複体とコチェイン複体の論理インデックス付けと印刷は異なります。詳細については `Hecke.ComplexOfMorphisms` を参照してください。
