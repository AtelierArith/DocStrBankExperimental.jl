```
conj(g::T, h::T) where {T <: GroupElem}
```

`g`を`h`で共役させたもの、すなわち`inv(h)*g*h`を返します。
