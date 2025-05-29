```
cholinv_logdet(input)
```

入力行列 `input` の逆行列と行列式の自然対数を同時に計算します。これはコレスキー因子分解を使用します。

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_inv, logdet_A = cholinv_logdet(A);

julia> isapprox(A_inv * A, I)
true

julia> isapprox(logdet_A, log(det(A)))
true
```
