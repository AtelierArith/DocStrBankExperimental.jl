```
TTrank(X::TTtensor,full=false)
TTrank(X::CoreCell,full=false)
```

Xの表現的TTランク。XのコアがサイズR{n-1} x In x Rnの場合、full=falseのときは(R1,...,R{n-1})を、full=trueのときは(1,R1,....,Rn)を返します。
