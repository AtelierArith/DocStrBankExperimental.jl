```
coprime_base(A::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
coprime_base(A::Vector{AbsSimpleNumFieldOrderElem}) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

$$
A
$$

の（主）イデアルのための互いに素な基底、すなわち、返される配列は入力と同じイデアルを乗法的に生成し、互いに素です。
