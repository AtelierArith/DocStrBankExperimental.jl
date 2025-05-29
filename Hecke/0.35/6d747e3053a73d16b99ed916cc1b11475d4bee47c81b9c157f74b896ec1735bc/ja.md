```
induce_rational_reconstruction(a::Generic.Poly{AbsSimpleNumFieldElem}, M::ZZRingElem) -> bool, Generic.Poly{AbsSimpleNumFieldElem}
```

$$
a
$$

の係数に有理再構成を適用します。係数が整数であると暗黙的に仮定しています（チェックは行われません）。すべての係数に対して成功した場合はtrueを返します。
