```
powerIterations(H::Union{ℍ{T}, 𝕄{T}}, q::Int;
<
evalues=false,
tol::Real=0,
maxiter::Int=300,
verbose=false>) where T<:RealOrComplex

powerIterations(L::𝕃{S}, q::Int;
< same optional keyword arguments in (1)>) where S<:Real
```

**エイリアス**: `powIter`

(1) 実数または複素数の `Hermitian` または `Matrix` $H$ の $q$ 最大（実数）固有値に関連する $q$ 固有ベクトルを計算します。これは、Strang によって提案された [power iterations](https://bit.ly/2JSo0pb) + [Gram-Schmidt orthogonalization](https://bit.ly/2YE6zvy) を使用します。固有ベクトルは $H$ の要素と同じ型で返されます。

$$
H
$$

は実数の固有値を持つ必要があります。つまり、実数の場合は対称行列であり、複素数の場合はエルミート行列である必要があります。

(2) (1) と同様ですが、行列の `LowerTriangular` ビュー $L$ のみを使用します。このオプションは実数行列にのみ利用可能です（以下を参照）。

以下は *<オプションのキーワード引数>* です：

  * `tol` はパワー法の収束のための許容誤差です（以下を参照）。
  * `maxiter` はパワー法に許可される最大反復回数です。
  * `verbose=true` の場合、すべての反復の収束が印刷されます。
  * `evalues=true` の場合、4タプル$(Λ, U, iterations, covergence)$が返されます。
  * `evalues=false` の場合、3タプル$(U, iterations, covergence)$が返されます。

!!! note "Nota Bene"
    [`evd`](@ref) 関数とは異なり、固有ベクトルと固有値は固有値の降順でソートされます。

    $$
    H
    $$

    が `Hermitian` で実数の場合、パワー反復の計算にはその下三角部分のみが使用されます（2のように）。この場合、[BLAS.symm](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.symm) ルーチンが使用されます。それ以外の場合は、[BLAS.gemm](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.gemm) ルーチンが使用されます。 [Threads](@ref) を参照してください。

    $$
    tol
    $$

    は $H$ の型の `Base.eps` の平方根の 100 倍にデフォルト設定されています。これは、相対収束基準が約半分の有効数字から 2 を引いた値で消失することを要求することに相当します。


**参照**: [`mgs`](@ref).

**例**

```julia
using LinearAlgebra, PosDefManifold
# エルミート（複素数）行列を生成
H=randP(ComplexF64, 10);
# 3 つの固有ベクトルと固有値
U, iterations, convergence=powIter(H, 3, verbose=true)
# すべての固有ベクトル
Λ, U, iterations, convergence=powIter(H, size(H, 2), evalues=true, verbose=true);
U'*U ≈ I && U*Λ*U'≈H ? println(" ⭐ ") : println(" ⛔ ")

# `Matrix` オブジェクトを渡す
Λ, U, iterations, convergence=powIter(Matrix(H), 3, evalues=true)

# `LowerTriangular` オブジェクトを渡す（この場合は実数行列である必要があります）
L=𝕃(randP(10))
Λ, U, iterations, convergence=powIter(L, 3, evalues=true)
```
