```
conj!(out::T, g::T, h::T) where {T <: GroupElem}
```

`inv(h)*g*h`を返します。`out`の変更が可能です。`g`または`h`が`out`とエイリアスされることは許可されています。
