```
dixon_solve(::Val{N}, A::SparseMatrixCSC{Int,Int}, Y::Matrix{Int}) where N
```

ディクソン法を使用して、`A*X = Y` の線形システムのための特化型ソルバー。ここで、`A` はスパース整数の `n×n` 行列であり、`Y` は密な整数の `n×N` 行列です。

`X` を `Matrix{Rational{Int64}}`、`Matrix{Rational{Int128}}`、または `Matrix{Rational{BigInt}}` のいずれかとして返します。すべての値を保持できる最小の型を選択します。

`A` が逆行列を持たない場合は空の行列を返します。

!!! warning
    `A` は正方行列でなければならず、`N` は `size(Y)[2]` と等しくなければならないため、そうでない場合は関数が失敗したり、エラーが発生したり、通知なしに静かに破損する可能性があります。

