```
orthogonalize(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, x
orthogonalize!!(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, x

orthogonalize(v, q, algorithm::Orthogonalizer]) -> w, s
orthogonalize!!(v, q, algorithm::Orthogonalizer]) -> w, s
```

ベクトル `v` を直交基底 `b` のすべてのベクトルに対して、タイプ [`Orthogonalizer`](@ref) の直交化アルゴリズム `alg` を使用して直交化し、結果のベクトル `w` と `v` と基底ベクトル `b` との重なり係数 `x` を返します。

`orthogonalize!` の場合、ベクトル `v` はその場で変更されます。両方の関数では、重なり係数 `x` のストレージをオプション引数 `x::AbstractVector` として提供でき、`length(x) >= length(b)` である必要があります。

与えられたベクトル `q`（正規化されていると仮定）に対して `v` を直交化することもでき、その場合、直交ベクトル `w` と `v` と `q` との内積 `s` が返されます。

`w` は正規化されていないことに注意してください。詳細は [`orthonormalize`](@ref) を参照してください。

可能な直交化アルゴリズムに関する詳細は、[`Orthogonalizer`](@ref) とその具体的なサブタイプ [`ClassicalGramSchmidt`](@ref)、[`ModifiedGramSchmidt`](@ref)、[`ClassicalGramSchmidt2`](@ref)、[`ModifiedGramSchmidt2`](@ref)、[`ClassicalGramSchmidtIR`](@ref) および [`ModifiedGramSchmidtIR`](@ref) を参照してください。
