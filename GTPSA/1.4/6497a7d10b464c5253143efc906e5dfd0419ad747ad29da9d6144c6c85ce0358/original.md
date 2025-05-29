```
integ!(t::TPS{T}, t1::TPS{T}, var=1) where {T} -> t
∫!(t::TPS{T}, t1::TPS{T}, var=1) where {T} -> t
```

Integrates `t1` wrt the variable `var` and sets `t` equal to the result. 
