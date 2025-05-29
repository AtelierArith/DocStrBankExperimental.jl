```
matrix_algebra(R::Ring, S::NCRing, gens::Vector{<: MatElem};
               isbasis::Bool = false)
  -> MatAlgebra
```

$$
S
$$

上の行列代数を返します。これは、`gens`の行列によって生成され、基底環$R$を持つ代数です。$S$は$R$上の代数であると仮定されています。`isbasis`が`true`の場合、与えられた行列がこの代数の$R$-基底であると仮定され、すなわち、生成された$R$-モジュールが乗法の下で閉じていることを意味します。
