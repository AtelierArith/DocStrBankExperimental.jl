```
div(f::T, g::T) where T <: RingElem
```

$$
f
$$

を$g$で割ったユークリッド商を返します。$g$がゼロの場合は`DivideError`がスローされるべきです。
