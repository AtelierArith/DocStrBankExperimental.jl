```
ILUZeroPreconditioner(;valuetype=Float64,indextype=Int64)
ILUZeroPreconditioner(matrix)
```

ゼロフィルインを使用した不完全LU前処理器で、[ILUZero.jl](https://github.com/mcovalt/ILUZero.jl)を使用しています。この前処理器は、オフダイアゴナルエントリへの更新を計算して保存するため、[`ILU0Preconditoner`](@ref)よりも優れた収束を提供します。
