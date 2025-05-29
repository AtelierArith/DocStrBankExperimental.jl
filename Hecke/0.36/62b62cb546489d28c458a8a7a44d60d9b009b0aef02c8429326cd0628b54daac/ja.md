```
is_norm(K::AbsSimpleNumField, a::ZZRingElem; extra::Vector{ZZRingElem}) -> Bool, AbsSimpleNumFieldElem
```

ZZRingElem $a$ に対して、$N(T) = a$ が成り立つ $T \in K$ を見つけることを試みます。成功した場合は true と $T$ を返し、そうでない場合は false といくつかの要素を返します。 \testtt{extra} には解に現れることが許可されている追加の素数を渡すことができます。これにより補足されます。要素は因数分解された形で返されます。
