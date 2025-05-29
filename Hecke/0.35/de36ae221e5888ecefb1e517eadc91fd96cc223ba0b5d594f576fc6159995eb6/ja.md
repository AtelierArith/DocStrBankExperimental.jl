```
modular_init(K::AbsSimpleNumField, p::ZZRingElem) -> modular_env
modular_init(K::AbsSimpleNumField, p::Integer) -> modular_env
```

数体 $K$ と「簡単な」素数 $p$（すなわち、\code{Int} に収まり、かつ多項式の判別式と互いに素である）を与えられたとき、$p$ の上にある関連する素イデアルの剰余類体を計算します。 \code{modular*proj} および \code{modular*lift} で使用できるデータを返します。
