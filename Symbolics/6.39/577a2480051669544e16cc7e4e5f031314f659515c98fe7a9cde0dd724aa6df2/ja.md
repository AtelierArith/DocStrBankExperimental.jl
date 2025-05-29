```julia
semiquadratic_form(
    exprs,
    vars
) -> Tuple{SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, SparseArrays.SparseMatrixCSC{Symbolics.Num, Int64}, Any, Any}

```

4つのオブジェクトのタプルを返します：

1. 次元 (m x n) の行列 `A`
2. 次元 (m x (n+1)*n/2) の行列 `B`
3. 長さ (n+1)*n/2 のベクトル `v2` で、`vars` の次数 2 までの単項式を含み、必要ないところはゼロ
4. 長さ m の残差ベクトル `c`

ここで、`n == length(exprs)` および `m == length(vars)` です。

結果は、`A * vars + B * v2 + c` が `exprs` と同じになるように配置されています。
