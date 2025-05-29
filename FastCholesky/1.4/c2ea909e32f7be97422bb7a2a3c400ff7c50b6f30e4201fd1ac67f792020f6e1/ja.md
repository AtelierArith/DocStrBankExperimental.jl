```
chollogdet(input)
```

入力行列 `input` の対数行列式をコレスキー分解を使用して計算します。この関数は `logdet(fastcholesky(input))` のエイリアスです。

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> logdet_A = chollogdet(A);

julia> isapprox(logdet_A, log(det(A)))
true
```
