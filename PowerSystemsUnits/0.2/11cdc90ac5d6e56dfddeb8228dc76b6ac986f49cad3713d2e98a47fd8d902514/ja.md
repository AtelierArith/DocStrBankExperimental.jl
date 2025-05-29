```
asqtype(x::T) where {T<:Unitful.Units} -> Type
```

Unitful量の「次元」から「量」への変換を行うヘルパー関数であり、これらは別々に扱われます。
