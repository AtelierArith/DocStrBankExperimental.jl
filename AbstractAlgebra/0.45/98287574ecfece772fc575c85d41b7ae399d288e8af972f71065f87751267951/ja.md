```
divrem(f::T, g::T) where T <: RingElem
```

$$
g
$$

がゼロの場合は`DivideError`をスローする必要があります。$f$を$g$で割ったユークリッド商と余りからなるペア`q, r`を返します。
