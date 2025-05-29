```
div_right!(out::T, g::T, h::T) where {T <: GroupElem}
```

`g*inv(h)`を返します。`out`を変更する可能性があります。`g`または`h`が`out`とエイリアスされることは許可されています。
