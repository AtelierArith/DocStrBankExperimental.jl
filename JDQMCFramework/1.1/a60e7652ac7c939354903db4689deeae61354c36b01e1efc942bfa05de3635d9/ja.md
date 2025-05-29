```
abstract type AbstractExactPropagator{T,E} <: AbstractPropagator{T,E} end
```

虚時間伝播子行列 $B$ を、正確に指数化されたホッピング行列 $K$ で定義するための抽象型。
