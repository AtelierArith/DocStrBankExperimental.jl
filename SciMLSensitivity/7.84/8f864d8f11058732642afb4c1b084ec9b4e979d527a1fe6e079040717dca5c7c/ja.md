```julia
InterpolatingAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

逆解ベクトル-ヤコビ行列の積のために前方解の補間を使用する接 adjoint 感度分析の実装です。デフォルトでは、前方パスの密な解が必要であり、勾配計算中に引数の保存を内部的に無視します。チェックポイントが有効になっている場合、チェックポイント間の補間に必要なメモリのみを要求します。

## コンストラクタ

```julia
InterpolatingAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing,
    checkpointing = false, noisemixing = false)
```

## キーワード引数

  * `autodiff`: ヤコビ行列を構築する必要がある場合、自動微分を使用します。デフォルトは `true` です。
  * `chunk_size`: フルヤコビ行列が構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false` および `autodiff=true`）。デフォルトは自動的なチャンクサイズの選択のための `0` です。
  * `diff_type`: フルヤコビ行列が必要な場合に FiniteDiff.jl がヤコビ行列を構築するために使用する方法です。`autodiff=false` の場合に適用されます。
  * `autojacvec`: 特別なシーディングを使用して自動微分を介してベクトル-ヤコビ行列の積（`J'*v`）を計算します。選択肢の全セットは次のとおりです：

      * `nothing`: 自動的に vjp を選択する自動アルゴリズムを使用します。これはデフォルトであり、ほとんどのユーザーに推奨されます。
      * `false`: ヤコビ行列は FiniteDiff.jl を介して構築されます。
      * `true`: ヤコビ行列は ForwardDiff.jl を介して構築されます。
      * `TrackerVJP`: vjp のために Tracker.jl を使用します。
      * `ZygoteVJP`: vjp のために Zygote.jl を使用します。
      * `EnzymeVJP`: vjp のために Enzyme.jl を使用します。
      * `ReverseDiffVJP(compile=false)`: vjp のために ReverseDiff.jl を使用します。`compile` はテープを事前コンパイルするかどうかのブール値で、`f` 関数に分岐（`if` または `while` 文）がない場合にのみ行うべきです。
  * `checkpointing`: 逆パスのためにチェックポイントが有効になっているかどうか。デフォルトは `false` です。
  * `noisemixing`: `du[i] = f(u[i])` の形でないノイズプロセスを処理します。たとえば、対角拡散を持つ SDE の感度を計算するために

    ```julia
    function g_mixing!(du, u, p, t)
        du[1] = p[3] * u[1] + p[4] * u[2]
        du[2] = p[3] * u[1] + p[4] * u[2]
        nothing
    end
    ```

    正しく、`noisemixing=true` を有効にする必要があります。デフォルトは `false` です。

vjp の選択肢に関する詳細については、感度アルゴリズムのドキュメントページまたは vjp タイプのドキュメント文字列を参照してください。

## チェックポイント

逆パスのメモリ使用量を削減するために、`InterpolatingAdjoint` にはチェックポイント機能が含まれています。`sol` が `dense` の場合、チェックポイントは無視され、任意の時間点で `u(t)` を計算するために連続解が使用されます。`checkpointing=true` で `sol` が `dense` でない場合、任意の時間点で `u(t)` を計算するために `sol.t[i]` と `sol.t[i+1]` の間の密な区間がオンデマンドで再構築されます。これにより、最大の時間間隔（必要なステップ数の観点から）にわたって密な解を保持するコストのみで、総メモリ要件が削減されます。総計算コストは元の前方計算コストの2倍を超えることはありません。

## SciMLProblem サポート

この `sensealg` は `ODEProblem`、`SDEProblem`、および `RODEProblem` のみをサポートします。この `sensealg` はコールバック（イベント）をサポートします。

### `SDEProblem` に関する免責事項

このアルゴリズムの実行時間は、対角ノイズ SDE に対して O(n^2) です。問題 #854 が解決されるまで。

## 参考文献

Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892
