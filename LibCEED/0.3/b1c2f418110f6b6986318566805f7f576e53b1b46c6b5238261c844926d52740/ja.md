```
apply(b::Basis, u::AbstractVector; nelem=1, tmode=NOTRANSPOSE, emode=EVAL_INTERP)
```

上記で定義された [`apply!`](@ref apply!(b::Basis, nelem, tmode::TransposeMode, emode::EvalMode, u::AbstractCeedVector, v::AbstractCeedVector)) と同じ機能を実行しますが、便利さのためにJulia配列から自動的に [`CeedVector`](@ref) に変換します。

結果は、正しいサイズの新しく割り当てられた配列に返されます。
