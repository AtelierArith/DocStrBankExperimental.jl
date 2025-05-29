```
conjugate_residual(TpM::TangentSpace, A, b, X=zero_vector(TpM))
conjugate_residual(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X=zero_vector(TpM))
conjugate_residual!(TpM::TangentSpace, A, b, X)
conjugate_residual!(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X)
```

$$
\mathcal A(p)[X] + b(p) = 0_p
$$

の解を計算します。ここで、

  * $$
    \mathcal A
    $$

    は $T_{p}\mathcal M$ 上の線形対称演算子です。
  * $$
    b
    $$

    は多様体上のベクトル場です。
  * $$
    X ∈ T_{p}\mathcal M
    $$

    は接ベクトルです。
  * $$
    0_p
    $$

    はゼロベクトル $T_{p}\mathcal M$ です。

この実装は [LaiYoshise:2024](@cite) のアルゴリズム 3 に従い、$X^{(0)}$ をゼロベクトルとして初期化されます。

  * 初期残差 $r^{(0)} = -b(p) - \mathcal A(p)[X^{(0)}]$
  * 初期共役方向 $d^{(0)} = r^{(0)}$
  * 初期化 $Y^{(0)} = \mathcal A(p)[X^{(0)}]$

以下のステップを $k=0,…$ のイテレーションで `stopping_criterion` が満たされるまで実行します。

1. ステップサイズ $α_k = \displaystyle\frac{⟨ r^{(k)}, \mathcal A(p)[r^{(k)}] ⟩_p}{⟨ \mathcal A(p)[d^{(k)}], \mathcal A(p)[d^{(k)}] ⟩_p}$ を計算します。
2. ステップ $X^{(k+1)} = X^{(k)} + α_kd^{(k)}$ を行います。
3. 残差を更新します $r^{(k+1)} = r^{(k)} + α_k Y^{(k)}$。
4. $$
    Z = \mathcal A(p)[r^{(k+1)}]
    $$

    を計算します。
5. 共役係数を更新します $β_k = \displaystyle\frac{⟨ r^{(k+1)}, \mathcal A(p)[r^{(k+1)}] ⟩_p}{⟨ r^{(k)}, \mathcal A(p)[r^{(k)}] ⟩_p}$。
6. 共役方向を更新します $d^{(k+1)} = r^{(k+1)} + β_kd^{(k)}$。
7. $$
    Y^{(k+1)} = -Z + β_k Y^{(k)}
    $$

    を更新します。

ステップ 7 の右辺は $\mathcal A[d^{(k+1)}]$ を評価するのと同じですが、実際の評価を回避します。

# 入力

  * `TpM` は [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`) であり、ドメインとして使用されます。
  * `A` は接空間上の対称線形演算子 `(M, p, X) -> Y` です。
  * `b` は接空間上のベクトル場 `(M, p) -> X` です。
  * `X` は初期接ベクトルです。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルがその結果を割り当てるか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`, ここで `c` は $\lVert b \rVert_{}$: 停止基準が満たされることを示すファンクタです。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。
