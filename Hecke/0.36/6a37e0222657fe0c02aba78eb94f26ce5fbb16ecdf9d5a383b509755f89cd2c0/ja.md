```
order(A::AbstractAssociativeAlgebra{QQFieldElem}, M::QQMatrix; check::Bool = true,
      cached::Bool = true)
  -> AlgAssAbsOrd
```

$$
A
$$

の基底行列$M$の順序を返します。`check`が設定されている場合、$M$が順序を定義しているかどうかがチェックされます。
