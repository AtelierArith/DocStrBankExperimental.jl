```
orthonormalize(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, β, x
orthonormalize!!(v, b::OrthonormalBasis, [x::AbstractVector,] alg::Orthogonalizer]) -> w, β, x

orthonormalize(v, q, algorithm::Orthogonalizer]) -> w, β, s
orthonormalize!!(v, q, algorithm::Orthogonalizer]) -> w, β, s
```

ベクトル `v` を直交基底 `b` のすべてのベクトルに対して直交化アルゴリズム `alg` を使用して直交正規化し、結果のベクトル `w`（ノルム1）、直交化後のノルム `β`、および `v` と基底ベクトル `b` との重なり係数 `x` を返します。すなわち、`v = β * w + b * x` です。

`orthogonalize!` の場合、ベクトル `v` はその場で変更されます。両方の関数では、重なり係数 `x` のストレージをオプション引数 `x::AbstractVector` として提供でき、`length(x) >= length(b)` である必要があります。

与えられたベクトル `q`（正規化されていると仮定）に対して `v` を直交正規化することもできます。この場合、直交正規化されたベクトル `w`、正規化前のノルム `β`、および `v` と `q` との内積 `s` が返されます。

`w` を正規化する必要がない場合は、[`orthogonalize`](@ref) を参照してください。

可能な直交化アルゴリズムに関する詳細については、[`Orthogonalizer`](@ref) およびその具体的なサブタイプである [`ClassicalGramSchmidt`](@ref)、[`ModifiedGramSchmidt`](@ref)、[`ClassicalGramSchmidt2`](@ref)、[`ModifiedGramSchmidt2`](@ref)、[`ClassicalGramSchmidtIR`](@ref)、[`ModifiedGramSchmidtIR`](@ref) を参照してください。
