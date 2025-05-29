```
gaussCoeffOf(b::FloatingGTBasisFuncs{T}) -> Matrix{T}
```

`b`内の各[`GaussFunc`](@ref)の指数と収束係数を返します（返される`Matrix`の各行に）。
