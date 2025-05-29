```
rational_reconstruction(A::SRow{ZZRingElem}, M::ZZRingElem) -> Bool, SRow{ZZRingElem}, ZZRingElem
```

$$
A
$$

のエントリに有理再構成を適用します。成功した場合はtrueを返します。この場合、分子は行列として返され、共通の分母は3番目の値として返されます。
