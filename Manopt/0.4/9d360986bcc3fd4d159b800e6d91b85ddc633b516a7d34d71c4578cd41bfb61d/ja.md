```
ChambollePockState <: AbstractPrimalDualSolverState
```

は、線形化されたまたは正確なChambolle Pock内のすべてのオプションと変数を格納します。以下のリストは、コンストラクタの順序を提供しており、前の反復は自動的に初期化され、デフォルトの値を持つものは省略できます。

  * `m`:                              基本点 $\mathcal M$ 上
  * `n`:                              基本点 $\mathcal N$ 上
  * `p`:                              初期点 $x^{(0)} ∈\mathcal M$ （およびその前の反復）
  * `X`:                              初期接ベクトル $X^{(0)}∈T^*\mathcal N$ （およびその前の反復）
  * `pbar`:                           次の双対更新ステップで使用される緩和反復（`:primal`緩和を使用する場合）
  * `Xbar`:                           次の原始更新ステップで使用される緩和反復（`:dual`緩和を使用する場合）
  * `primal_stepsize`:                （`1/sqrt(8)`）原始近接の近接パラメータ
  * `dual_stepsize`:                  （`1/sqrt(8)`）双対近接の近接パラメータ
  * `acceleration`:                   （`0.`）Chambolle & Pockによる加速因子
  * `relaxation`:                     （`1.`）原始緩和ステップでの緩和（`pbar`を計算するため）
  * `relax`:                          （`:primal`）緩和する変数（`:primal`または`:dual`）
  * `stop`:                           a [`StoppingCriterion`](@ref)
  * `variant`:                        （`exact`）`:exact`または`:linearized` Chambolle-Pockを実行するかどうか
  * `update_primal_base`:             （`(p,o,i) -> o.m`）原始基底を更新する関数
  * `update_dual_base`:               （`(p,o,i) -> o.n`）双対基底を更新する関数
  * `retraction_method`:              （`default_retraction_method(M, typeof(p))`）使用する再収縮
  * `inverse_retraction_method`:      （`default_inverse_retraction_method(M, typeof(p))`）多様体 $\mathcal M$ 上で使用する逆再収縮。
  * `inverse_retraction_method_dual`: （`default_inverse_retraction_method(N, typeof(n))`）多様体 $\mathcal N$ 上で使用する逆再収縮。
  * `vector_transport_method`:        （`default_vector_transport_method(M, typeof(p))`）多様体 $\mathcal M$ 上で使用するベクトル輸送。
  * `vector_transport_method_dual`:   （`default_vector_transport_method(N, typeof(n))`）多様体 $\mathcal N$ 上で使用するベクトル輸送。

最後の2つの関数については、[`AbstractManoptProblem`](@ref)`p`、[`AbstractManoptSolverState`](@ref)`o`、および現在の反復 `i` が引数です。これらをデフォルトの恒等式とは異なるようにアクティブにする場合、アルゴリズムが機能するために `p.Λ` を提供する必要があります（これは線形化された場合に `missing` である可能性があります）。

# コンストラクタ

```
ChambollePockState(M::AbstractManifold, N::AbstractManifold,
    m::P, n::Q, p::P, X::T, primal_stepsize::Float64, dual_stepsize::Float64;
    kwargs...
)
```

ここで、他のすべてのフィールドはキーワード引数であり、デフォルト値は括弧内に示されています。

`Manifolds.jl` がロードされている場合、`N` もキーワード引数であり、デフォルトで `TangentBundle(M)` に設定されています。
