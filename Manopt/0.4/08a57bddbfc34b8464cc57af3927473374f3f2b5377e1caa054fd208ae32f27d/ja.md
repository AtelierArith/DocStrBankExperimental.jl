```
conjugate_residual(TpM::TangentSpace, A, b, p=rand(TpM))
conjugate_residual(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, p=rand(TpM))
conjugate_residual!(TpM::TangentSpace, A, b, p)
conjugate_residual!(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, p)
```

$$
\mathcal A(p)[X] + b(p) = 0_p
$$

の解を計算します。ここで、

  * $$
    \mathcal A
    $$

    は $T_p\mathcal M$ 上の線形対称演算子です。
  * $$
    b
    $$

    は多様体上のベクトル場です。
  * $$
    X ∈ T_p\mathcal M
    $$

    は接ベクトルです。
  * $$
    0_p
    $$

    はゼロベクトル $T_p\mathcal M$ です。

この実装は [LaiYoshise:2024](@cite) のアルゴリズム3に従い、$X^{(0)}$ をゼロベクトルとして初期化し、

  * 初期残差 $r^{(0)} = -b(p) - \mathcal A(p)[X^{(0)}]$
  * 初期共役方向 $d^{(0)} = r^{(0)}$
  * 初期化 $Y^{(0)} = \mathcal A(p)[X^{(0)}]$

は、`stopping_criterion` が満たされるまで、反復 $k=0,…$ で以下のステップを実行します。

1. ステップサイズ $α_k = \displaystyle\frac{\langle r^{(k)}, \mathcal A(p)[r^{(k)}] \rangle_p}{\langle \mathcal A(p)[d^{(k)}], \mathcal A(p)[d^{(k)}] \rangle_p}$ を計算します。
2. ステップ $X^{(k+1)} = X^{(k)} + α_kd^{(k)}$ を行います。
3. 残差を更新 $r^{(k+1)} = r^{(k)} + α_k Y^{(k)}$ します。
4. $$
    Z = \mathcal A(p)[r^{(k+1)}]
    $$

    を計算します。
5. 共役係数を更新 $β_k = \displaystyle\frac{\langle r^{(k+1)}, \mathcal A(p)[r^{(k+1)}] \rangle_p}{\langle r^{(k)}, \mathcal A(p)[r^{(k)}] \rangle_p}$ します。
6. 共役方向を更新 $d^{(k+1)} = r^{(k+1)} + β_kd^{(k)}$ します。
7. $$
    Y^{(k+1)} = -Z + β_k Y^{(k)}
    $$

    を更新します。

ステップ7の右辺は $\mathcal A[d^{(k+1)}]$ を評価するのと同じですが、実際の評価を回避します。

# 入力

  * `TpM` は [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`) であり、ドメインとして使用されます。
  * `A` は接空間上の対称線形演算子 `(M, p, X) -> Y` です。
  * `b` は接空間上のベクトル場 `(M, p) -> X` です。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref) は `A` と `b` が割り当てを行うか、インプレースで実装されているかを指定します。
  * `stopping_criterion::`[`StoppingCriterion`](@ref)`=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref ManifoldsBase.manifold_dimension-Tuple{AbstractManifold})`(TpM))`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`, ここで `c` は $\lVert b \rVert$ のノルムです。

# 出力

得られた（近似的な）最小化解 $X^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。
