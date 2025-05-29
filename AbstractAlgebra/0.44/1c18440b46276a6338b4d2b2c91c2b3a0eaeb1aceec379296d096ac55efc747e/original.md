```
conj(g::T, h::T) where {T <: GroupElem}
```

Return the conjugation of `g` by `h`, i.e. `inv(h)*g*h`.
