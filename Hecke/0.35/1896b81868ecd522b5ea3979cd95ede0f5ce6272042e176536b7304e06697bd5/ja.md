```
factor_coprime(Q::FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}
```

$$
Q
$$

の互いに素な因数分解：$Q$の各理想は\code{integral_split}を使用して分割され、その後、互いに素な基底が計算されます。これは{\bf いかなる因数分解も使用しません}。
