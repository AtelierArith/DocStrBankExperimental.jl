```
factor_coprime(I::AbsNumFieldOrderIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}, a::FacElem{AbsSimpleNumFieldElem, AbsSimpleNumField}) -> Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, ZZRingElem}
```

$$
a
$$

によって生成される主理想を互いに素なものに因数分解し、$a$の因数分解における主理想から互いに素な基底を計算することによって行います。
