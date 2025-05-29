```
wrapb(f::Function; time_agnostic=true)
```

`wrapb`は[`wrap`](@ref)のようなもので、ただし`f`はすべての入力値に対してブロードキャストされます。
