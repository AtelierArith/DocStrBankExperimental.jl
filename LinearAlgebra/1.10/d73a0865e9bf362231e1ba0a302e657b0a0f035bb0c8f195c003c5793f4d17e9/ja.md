```
issuccess(F::Factorization)
```

行列の因数分解が成功したかどうかをテストします。

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)` はJulia 1.6以降が必要です。


```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true

julia> F = lu([1 0; 0 0]; check = false);

julia> issuccess(F)
false
```
