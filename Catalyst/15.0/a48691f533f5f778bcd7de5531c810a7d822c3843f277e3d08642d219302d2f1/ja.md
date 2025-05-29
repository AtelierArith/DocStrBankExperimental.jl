```
isequivalent(rn1::ReactionSystem, rn2::ReactionSystem; ignorenames = true,
    debug = false)
```

2つの[`ReactionSystem`](@ref)の基盤となる種、パラメータ、および反応が同じであるかどうかをテストします。等価性をテストする際にシステムの名前は無視されます。

注意:

  * 現在、レートを簡略化しないため、`A^2+2*A+1`のレートは`(A+1)^2`とは異なると見なされます。
  * `ignorenames = false`は、サブシステムと親システムの等価性をチェックする際に使用されます。
  * `parent`システムが同じであるかどうかはチェックしません。
  * `debug = true`を渡すと、2つのシステムが異なると見なされる原因となったフィールドが出力されます。
