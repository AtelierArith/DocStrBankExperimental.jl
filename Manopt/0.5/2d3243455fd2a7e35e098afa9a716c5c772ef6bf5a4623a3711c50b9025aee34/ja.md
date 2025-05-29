```
get_jacobian(M::AbstractManifold, vgf::AbstractVectorGradientFunction, p; kwargs...)
get_jacobian(M::AbstractManifold, J, vgf::AbstractVectorGradientFunction, p; kwargs...)
```

マンifold `M` 上の点 `p` における [`AbstractVectorGradientFunction`](@ref) $F$ のヤコビ行列 $J_F ∈ ℝ^{m×n}$ を計算します。

ベクトル関数 $F: \mathcal M → ℝ^m$ のヤコビ行列には二つの解釈があります。どちらも接空間 $T_{p}\mathcal M$ 上の基底を選ぶことに依存し、これを $Y_1,…,Y_n$ と表記します。ここで `n` は [`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)``(M)` です。任意の接ベクトル $X = \displaystyle\sum_i c_iY_i$ と書くことができます。

1. ヤコビ行列 $J_F$ は基底 $Y_1,…,Y_n$ に関する行列であり、次のようになります。

任意の $X∈T_{p}\mathcal M$ に対して、微分の等式 $DF(p)[X] = Jc$ が成り立ちます。言い換えれば、$J$ の `j` 番目の列は $DF(p)[Y_j]$ で与えられます。

2. 成分関数 $F_i: \mathcal M → ℝ$ の勾配 $\operatorname{grad} F_i(p)$ が与えられた場合、

ヤコビ行列関数を次のように定義します。

$$
math   J(X) = \begin{pmatrix} ⟨\operatorname{grad} F_1, X⟩_p\\ ⟨\operatorname{grad} F_1, X⟩_p\\ ⋮\\ ⟨\operatorname{grad} F_1, X⟩_p\end{pmatrix}
$$

この場合、$J_F$ の `j` 番目の列は $J(Y_i)$ で与えられるか、または $i$ 番目の行は $i$ 番目の勾配関数とすべての基底ベクトル $Y_j$ の内積 $\operatorname{grad} F_1, Y_j⟩_p$ で与えられます。

計算は `J` のインプレースで行うことができます。

# キーワード引数

  * `basis::AbstractBasis =`[`get_basis`](@ref)`(vgf)` ベクトル関数の勾配の [`CoordinateVectorialType`](@ref) に対する基底であり、この基底と座標が与えられた基底が一致しない場合、基底の変更が生じる可能性があります。
  * `range::AbstractPowerRepresentation =`[`get_range`](@ref)`(vgf.jacobian_type)` 勾配の範囲を指定します。これは [`FunctionVectorialType`](@ref) の場合、勾配が与えられるべき冪多様体のタイプです。
