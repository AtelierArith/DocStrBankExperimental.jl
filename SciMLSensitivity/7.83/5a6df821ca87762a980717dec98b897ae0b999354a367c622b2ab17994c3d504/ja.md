```julia
BacksolveAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

ODEの逆解法を用いたアジョイント感度分析の実装です。デフォルトでは、このアルゴリズムは前方パスからの値を使用して逆解を正しい位置に摂動させ、メモリを削減します（O(1)メモリ）。チェックポイント安定化が含まれており、単純な実装に比べて追加の数値的安定性を提供します。

## コンストラクタ

```julia
BacksolveAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing,
    checkpointing = true, noisemixing = false)
```

## キーワード引数

  * `autodiff`: ヤコビアンを構築する必要がある場合、自動微分を使用します。デフォルトは`true`です。
  * `chunk_size`: フルヤコビアンが構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false`かつ`autodiff=true`）。デフォルトは`0`で、チャンクサイズの自動選択です。
  * `diff_type`: フルヤコビアンが必要な場合にFiniteDiff.jlがヤコビアンを構築するために使用する方法（`autodiff=false`）。
  * `autojacvec`: 特別なシーディングを用いて自動微分でベクトル-ヤコビアン積（`J'*v`）を計算します。選択肢の全セットは以下の通りです：

      * `nothing`: 自動アルゴリズムを使用してvjpを自動的に選択します。これはデフォルトであり、ほとんどのユーザーに推奨されます。
      * `false`: ヤコビアンはFiniteDiff.jlを介して構築されます。
      * `true`: ヤコビアンはForwardDiff.jlを介して構築されます。
      * `TrackerVJP`: vjpのためにTracker.jlを使用します。
      * `ZygoteVJP`: vjpのためにZygote.jlを使用します。
      * `EnzymeVJP`: vjpのためにEnzyme.jlを使用します。
      * `ReverseDiffVJP(compile=false)`: vjpのためにReverseDiff.jlを使用します。`compile`はテープを事前コンパイルするかどうかのブール値で、`f`関数に分岐（`if`や`while`文）がない場合にのみ行うべきです。
  * `checkpointing`: 逆パスのためにチェックポイントが有効かどうか。デフォルトは`true`です。
  * `noisemixing`: `du[i] = f(u[i])`の形でないノイズプロセスを処理します。例えば、対角拡散を持つSDEの感度を計算するためには

    ```julia
    function g_mixing!(du, u, p, t)
        du[1] = p[3] * u[1] + p[4] * u[2]
        du[2] = p[3] * u[1] + p[4] * u[2]
        nothing
    end
    ```

    正しく、`noisemixing=true`を有効にする必要があります。デフォルトは`false`です。

vjpの選択肢に関する詳細については、感度アルゴリズムのドキュメントページまたはvjpタイプのドキュメント文字列を参照してください。

## Backsolveの適用性と注意

`BacksolveAdjoint`が適用可能な場合、それは高速な方法であり、最も少ないメモリを必要とします。しかし、すべてのODEが大多数のODEソルバーによる逆積分の下で安定しているわけではないため、注意が必要です。そのような方程式の例はローレンツ方程式です。ローレンツ方程式を前方に解き、その後任意の適応時間ステップと非可逆的な積分器で逆に解くと、逆解は前方解から逸脱します。簡単なデモンストレーションとして：

```julia
using Sundials
function lorenz(du, u, p, t)
    du[1] = 10.0 * (u[2] - u[1])
    du[2] = u[1] * (28.0 - u[3]) - u[2]
    du[3] = u[1] * u[2] - (8 / 3) * u[3]
end
u0 = [1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = ODEProblem(lorenz, u0, tspan)
sol = solve(prob, Tsit5(), reltol = 1e-12, abstol = 1e-12)
prob2 = ODEProblem(lorenz, sol.u[end], (100.0, 0.0))
sol = solve(prob, Tsit5(), reltol = 1e-12, abstol = 1e-12)
@show sol.u[end] - u0 #[-3.22091, -1.49394, 21.3435]
```

したがって、この方法を有効にする前に、自分の問題のタイプに対するバックソルブの安定性を確認する必要があります。さらに、バックソルブとともにチェックポイントを使用することは、安定化のための低メモリの方法となる可能性があります。

このトピックに関する詳細については、[Stiff Neural Ordinary Differential Equations](https://aip.scitation.org/doi/10.1063/5.0060697)を参照してください。

## チェックポイント

逆パスの数値的安定性を向上させるために、`BacksolveAdjoint`にはチェックポイント機能が含まれています。`sol.u`が時系列である場合、逆に進む際に時間`sol.t`がヒットするたびに、コールバックが逆のODE部分を`sol.u[i]`で置き換えます。これにより、解が適切な軌道に戻され、ドリフトによって引き起こされる数値的誤差が減少します。

## SciMLProblemサポート

この`sensealg`は`ODEProblem`、`SDEProblem`、および`RODEProblem`のみをサポートします。この`sensealg`はコールバック関数（イベント）をサポートします。

### `SDEProblem`に関する免責事項

このアルゴリズムの実行時間は、問題#854が解決されるまで、対角ノイズSDEに対してO(n^2)です。

## 参考文献

ODE: Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Chen, R.T.Q. and Rubanova, Y. and Bettencourt, J. and Duvenaud, D. K., Neural ordinary differential equations. In Advances in neural information processing systems, pp. 6571–6583 (2018)

Pontryagin, L. S. and Mishchenko, E.F. and Boltyanskii, V.G. and Gamkrelidze, R.V. The mathematical theory of optimal processes. Routledge, (1962)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892

DAE: Cao, Y. and Li, S. and Petzold, L. and Serban, R., Adjoint sensitivity analysis for differential-algebraic equations: The adjoint DAE system and its numerical solution, SIAM journal on scientific computing 24 pp: 1076-1089 (2003)

SDE: Gobet, E. and Munos, R., Sensitivity Analysis Using Ito-Malliavin Calculus and Martingales, and Application to Stochastic Optimal Control, SIAM Journal on control and optimization, 43, pp. 1676-1713 (2005)

Li, X. and Wong, T.-K. L.and Chen, R. T. Q. and Duvenaud, D., Scalable Gradients for Stochastic Differential Equations, PMLR 108, pp. 3870-3882 (2020), http://proceedings.mlr.press/v108/li20i.html ```
