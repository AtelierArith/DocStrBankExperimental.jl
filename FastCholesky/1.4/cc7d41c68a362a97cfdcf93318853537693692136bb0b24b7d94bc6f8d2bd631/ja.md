```
cholinv(input)
```

入力行列 `input` の逆行列をコレスキー分解を使用して計算します。この関数は `inv(fastcholesky(input))` のエイリアスです。

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_inv = cholinv(A);

julia> A_inv ≈ inv(A)
true
```
