```
conj(g::T, h::T) where {T <: GroupElem}
```

`g`を`h`で共役させたものを返します。すなわち、`inv(h)*g*h`です。
