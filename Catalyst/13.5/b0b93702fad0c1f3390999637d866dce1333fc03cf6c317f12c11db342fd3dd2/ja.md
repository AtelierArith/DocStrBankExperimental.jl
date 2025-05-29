```
isequivalent(rn1::ReactionSystem, rn2::ReactionSystem; ignorenames = true)
```

2つの[`ReactionSystem`](@ref)の基盤となる種、パラメータ、および反応が同じであるかどうかをテストします。等価性のテストではシステムの名前は無視されます。

注意:

  * 現在、レートを簡略化しないため、`A^2+2*A+1`のレートは`(A+1)^2`とは異なると見なされます。
  * 等価性を判断する際に`defaults`は含まれません。
