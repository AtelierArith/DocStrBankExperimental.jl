```
ILUZeroPreconditioner()
ILUZeroPreconditioner(matrix)
```

ゼロフィルインを使用した不完全LU前処理器で、 [ILUZero.jl](https://github.com/mcovalt/ILUZero.jl) を使用しています。この前処理器はオフダイアゴナルエントリの更新を計算して保存するため、 [`ILU0Preconditioner`](@ref) よりも優れた収束を提供します。
