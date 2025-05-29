```
rational_reconstruction(A::SRow{ZZRingElem}, M::ZZRingElem) -> Bool, SRow{ZZRingElem}, ZZRingElem
```

行列 $A$ の要素に有理数再構成を適用します。成功した場合に限り真を返します。この場合、分子は行列として返され、共通の分母は3番目の値として返されます。
