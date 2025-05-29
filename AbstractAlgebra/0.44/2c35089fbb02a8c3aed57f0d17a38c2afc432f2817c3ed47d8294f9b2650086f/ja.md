```
comm!(out::T, g::T, h::T) where {T <: GroupElem}
```

`inv(g)*inv(h)*g*h` を返します。`out` を変更することがあるかもしれません。`g` または `h` を `out` とエイリアスすることは許可されています。
