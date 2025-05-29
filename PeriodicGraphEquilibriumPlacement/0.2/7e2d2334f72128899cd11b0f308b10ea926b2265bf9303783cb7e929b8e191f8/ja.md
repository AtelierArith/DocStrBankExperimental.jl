```
rational_solve(::Val{N}, A::SparseMatrixCSC{Int,Int}, Y::Matrix{Int}) where N
```

[`dixon_solve`](@ref) のフォールバックソルバーで、LU分解を行った後、前方および後方代入を実行します。`A` が逆行列でない場合は空の行列を返します。

一般的に、[`dixon_solve`](@ref) よりも遅くなります。

!!! warning
    `A` は正方行列でなければならず、`N` は `size(Y)[2]` と等しくなければならないため、関数が失敗したり、エラーが発生したり、通知なしに静かに破損する可能性があります。

