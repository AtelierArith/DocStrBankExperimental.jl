```
crt(r1::AbsSimpleNumFieldOrderElem, i1::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, r2::AbsSimpleNumFieldOrderElem, i2::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbsSimpleNumFieldOrderElem
```

$ x $ を見つけるために、$ x \equiv r*1 \bmod i*1 $ および $ x \equiv r*2 \bmod i*2 $ を満たすように `idempotents` を使用します。
