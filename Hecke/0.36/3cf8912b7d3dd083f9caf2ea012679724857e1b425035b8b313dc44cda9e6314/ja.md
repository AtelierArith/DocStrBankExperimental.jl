```
order(A::AbstractAssociativeAlgebra{QQFieldElem}, B::Vector{<: AbstractAssociativeAlgebraElem{QQFieldElem}}; check::Bool = true,
      isbasis::Bool = false, cached::Bool = true)
  -> AlgAssAbsOrd
```

$$
A
$$

によって生成される$B$の順序を返します。`check`が設定されている場合、$B$が順序を定義するかどうかがチェックされます。`isbasis`が設定されている場合、要素は$\mathbb Z$-基底を形成するものと見なされます。
