```
abstract type AbstractChkbrdPropagator{T,E} <: AbstractPropagator{T,E} end
```

虚時間伝播子行列 $B$ を表す抽象型で、チェッカーボード近似によって表される指数関数的ホッピング行列 $K$ で定義されています。
