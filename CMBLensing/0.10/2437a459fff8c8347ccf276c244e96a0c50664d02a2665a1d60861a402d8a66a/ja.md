```
batch(fs::LambertField...)
batch(fs::Vector{<:LambertField})
```

1つ以上のLambertFieldを「バッチ」次元（基になる配列の次元4）に沿って連結します。逆の操作については、[`unbatch`](@ref)を参照してください。
