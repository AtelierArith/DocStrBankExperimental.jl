```
cleanup!(M::AbstractArray{T}; tol = Base.rtoldefault(real(T)))
```

`M`の実部または虚部が`tol`より小さい場合、それをゼロにします。
