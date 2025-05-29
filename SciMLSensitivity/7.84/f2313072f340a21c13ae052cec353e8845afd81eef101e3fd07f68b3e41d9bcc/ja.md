```julia
QuadratureAdjoint{CS, AD, FDT, VJP} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

逆解の完全な連続解を展開してODE後の数値積分を実行するための随伴感度分析の実装です。この方法は密な解を必要とし、勾配計算中に引数の保存を無視します。コンストラクタ内の許容誤差は内部の数値積分を制御します。

この方法は、剛性/暗黙の方程式に対してO(n^3 + p)であり（BacksolveAdjointおよびInterpolatingAdjointのO((n+p)^3)スケーリングとは対照的）、したがって計算効率がはるかに高いです。しかし、密な逆パスを保持する必要があり、したがってメモリ集約型です。

## コンストラクタ

```julia
QuadratureAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = nothing, abstol = 1e-6,
    reltol = 1e-3)
```

## キーワード引数

  * `autodiff`: ヤコビアンを構築する必要がある場合、自動微分を使用してヤコビアンを構築します。デフォルトは`true`です。
  * `chunk_size`: フルヤコビアンが構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false`および`autodiff=true`）。デフォルトは自動的なチャンクサイズの選択のために`0`です。
  * `diff_type`: フルヤコビアンが必要な場合にFiniteDiff.jlによってヤコビアンを構築するために使用される方法（`autodiff=false`）。
  * `autojacvec`: 特別なシーディングを使用して自動微分を介してベクトル-ヤコビアン積（`J'*v`）を計算します。選択肢の全セットは次のとおりです：

      * `nothing`: 自動的にvjpを選択する自動アルゴリズムを使用します。これはデフォルトであり、ほとんどのユーザーに推奨されます。
      * `false`: ヤコビアンはFiniteDiff.jlを介して構築されます。
      * `true`: ヤコビアンはForwardDiff.jlを介して構築されます。
      * `TrackerVJP`: vjpのためにTracker.jlを使用します。
      * `ZygoteVJP`: vjpのためにZygote.jlを使用します。
      * `EnzymeVJP`: vjpのためにEnzyme.jlを使用します。
      * `ReverseDiffVJP(compile=false)`: vjpのためにReverseDiff.jlを使用します。`compile`はテープを事前コンパイルするかどうかのブール値で、`f`関数に分岐（`if`または`while`文）がない場合にのみ行うべきです。
  * `abstol`: 数値積分計算の絶対許容誤差
  * `reltol`: 数値積分計算の相対許容誤差

vjpの選択肢に関する詳細については、感度アルゴリズムのドキュメントページまたはvjpタイプのドキュメンテーションを参照してください。

## SciMLProblem サポート

この`sensealg`は`ODEProblem`のみをサポートします。この`sensealg`はイベント（コールバック）をサポートします。

## 参考文献

Rackauckas, C. and Ma, Y. and Martensen, J. and Warner, C. and Zubov, K. and Supekar, R. and Skinner, D. and Ramadhana, A. and Edelman, A., Universal Differential Equations for Scientific Machine Learning,	arXiv:2001.04385

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)

Rackauckas, C. and Ma, Y. and Dixit, V. and Guo, X. and Innes, M. and Revels, J. and Nyberg, J. and Ivaturi, V., A comparison of automatic differentiation and continuous sensitivity analysis for derivatives of differential equation solutions, arXiv:1812.01892

Kim, S., Ji, W., Deng, S., Ma, Y., & Rackauckas, C. (2021). Stiff neural ordinary differential equations. Chaos: An Interdisciplinary Journal of Nonlinear Science, 31(9), 093122.
