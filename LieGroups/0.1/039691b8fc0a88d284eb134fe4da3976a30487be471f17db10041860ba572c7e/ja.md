```
jacobian_conjugate(G::AbstractLieGroup, g, h; basis::AbstractBasis=DefaultLieAlgebraOrthogonalBasis(); X=zero_vector(LieAlgebar(G)))
jacobian_conjugate!(G::AbstractLieGroup, J, g, h; basis::AbstractBasis=DefaultLieAlgebraOrthogonalBasis(); X=zero_vector(LieAlgebar(G)))
```

[`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$ のヤコビ行列を、[`LieAlgebra`](@ref) の [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) に関して計算します。

デフォルトは、[`diff_conjugate`](@ref) $D(c_g(h))[X]$ を使用して実装されます：ヤコビ行列 $J$ の $j$ 番目の列は、基底 $B$ に関しての接ベクトル `D(c_g(h))[X_j]``の係数によって与えられます。ここで、``X_j``は``B``の``j`` 番目の基底ベクトルです。

!!! note
    `h` が [`Identity`](@ref) の場合と、$D(c_g(h))[X]$ と [`adjoint`](@ref) $\mathrm{Ad}(g)$ の関係において、ヤコビ行列は時々「随伴行列」と呼ばれます。例えば、[`hat`](@ref) と [`vee`](@ref) に使用される [`DefaultLieAlgebraOrthogonalBasis`](@ref)`()` を基底として選択する場合、[SolaDerayAtchuthan:2021](@cite) でそのように言及されています。


## キーワード引数

  * `X=zero_vector(LieAlgebra(G))` リー代数接ベクトルを格納するための一時メモリを渡します。

```
