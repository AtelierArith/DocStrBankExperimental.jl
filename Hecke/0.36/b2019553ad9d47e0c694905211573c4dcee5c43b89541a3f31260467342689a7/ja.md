```
matrix_algebra(R::Ring, gens::Vector{<: MatElem}; isbasis::Bool = false)
  -> MatAlgebra
```

$$
R
$$

上の行列代数を返します。これは`gens`にある行列によって生成されます。`isbasis`が`true`の場合、与えられた行列がこの代数の$R$-基底であると仮定されます。すなわち、生成された$R$-モジュールが乗法の下で閉じていることを意味します。
