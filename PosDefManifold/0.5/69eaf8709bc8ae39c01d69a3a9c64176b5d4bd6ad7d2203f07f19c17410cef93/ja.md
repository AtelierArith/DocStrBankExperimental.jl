```
choInv(P::AbstractArray{T};
	kind::Symbol = :LLt, tol::Real = √eps(T)) where T<:RealOrComplex
```

実数または複素数の正定値行列 $P$ に対して、$P=LL^H$ はその *コレスキー分解* であり、$P=L_1DL_1^H$ は関連する *LDLt* 分解です。上記では、$L$ は下三角行列、$D$ は正定値対角行列、$L_1$ は単位下三角行列です。返すものは：

  * `kind` が `:LLt` （デフォルト）の場合、2タプル $L$, $L^{-H}$
  * `kind` が `:LDLt` の場合、3タプル $L_1$, $D$, $L_1^{-H}$。

これらは一度のパスで得られ、小さな行列の場合、Juliaの [chelosky](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.cholesky) 関数を呼び出して下の因子を逆にするよりも速いです。ただし、次のように設定した場合を除きます。

```
 BLAS.set_num_threads(1).
```

入力行列 `P` は `Matrix` または `Hermitian` 型である可能性があります。下三角のみが使用されるため、`P` は正定値行列の `LowerTriangular` ビューでもかまいません。`P` が実数の場合、`Symmetric` 型でもかまいません。

アルゴリズムは *乗法的ガウス消去* です。完全に実行されると、入力行列 `P` の最後には単位行列が存在します。

**注意:** 出力 $L^{-H}$ は $P$ の逆平方根（ホワイトニング行列）であり、$L^{-1}PL^{-H}=I$ です。したがって、$P$ の逆は $P^{-1}=L^{-H}L^{-1}$ として得られます。これは計算される最も速いホワイトニング行列ですが、特に大きな行列に対しては数値精度が悪くなります。

次の関係が成り立ちます：

  * $$
    L=PL^{-H}
    $$
  * $$
    L^{H}=L^{-1}P
    $$
  * $$
    L^{-H}=P^{-1}L
    $$
  * $$
    L^{-1}=L^{H}P^{-1}
    $$

    。

また、次のこともあります：

  * $$
    L^{H}L=L^{-1}P^{2}L^{-H}=UPU^H
    $$

    、ここで $U$ は直交行列（以下参照）であり、
  * $$
    L^{-1}L^{-H}=L^{H}P^{-2}L=UP^{-1}U^H
    $$

    。

$$
LL^{H}
$$

と $L^{H}L$ はユニタリ相似であり、すなわち、

$$
ULL^{H}U^H=L^{H}L
$$

、

ここで $U=L^{-1}P^{1/2}$ であり、$P^{1/2}=H$ は $P$ の *主* （一意の対称）平方根です。これは $PP^{-1}=HHL^{-H}L^{-1}$ と書くことで見られます。両辺の左側に $L^{-1}$ を掛け、右側に $L$ を掛けると、

$$
L^{-1}PP^{-1}L=L^{-1}HHL^{-H}=I=(L^{-1}H)(L^{-1}H)^H
$$

となり、$L^{-1}H$ が正方行列であるため、ユニタリでなければなりません。

これらの式から次のことが得られます：

  * $$
    H=LU=U^HL^H
    $$
  * $$
    L=HU^H
    $$
  * $$
    H^{-1}=U^HL^{-1}
    $$
  * $$
    L^{-1}=UH^{-1}
    $$

    。

$$
U
$$

は $L^{H}$ の *極分解* であり、すなわち $L^{H}=UH$ です。なぜなら、$LL^{H}=HU^HUH^H=H^2=P$ だからです。

$$
L^{H}L=UCU^H
$$

から、$L^{H}LU=UC=ULL^{H}$ が得られ、$U=L^{-1}H$ から $L=HU^H$ が得られます。

**参照:** [`choInv!`](@ref), [`choL`](@ref)。

**例**

```julia
using PosDefManifold
n, t = 800, 6000
etol = 1e-9
Z=randn(t, n)
Y=Z'*Z
Yi=inv(Y)

A, B=choInv!(copy(Y))
norm(A*A'-Y)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(B*B'-Yi)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

A, D, B=choInv!(copy(Y); kind=:LDLt)
norm(Y-A*D*A')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(Yi-B*inv(D)*B')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

# 複素行列のテストを繰り返す
Z=randn(ComplexF64, t, n)
Y=Z'*Z
Yi=inv(Y)

A, B=choInv!(copy(Y))
norm(A*A'-Y)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(B*B'-Yi)/√n < etol ? println(" ⭐ ") : println(" ⛔ ")

A, D, B=choInv!(copy(Y); kind=:LDLt)
norm(Y-A*D*A')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
norm(Yi-B*inv(D)*B')/√n < etol ? println(" ⭐ ") : println(" ⛔ ")
```
