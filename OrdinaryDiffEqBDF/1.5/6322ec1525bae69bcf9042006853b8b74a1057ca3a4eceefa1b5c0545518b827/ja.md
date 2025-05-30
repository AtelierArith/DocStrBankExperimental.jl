```julia
ABDF2(; chunk_size = Val{0}(),
        autodiff = AutoForwardDiff(),
        standardtag = Val{true}(),
        concrete_jac = nothing,
        linsolve = nothing,
        precs = DEFAULT_PRECS,
        κ = nothing,
        tol = nothing,
        nlsolve = NLNewton(),
        smooth_est = true,
        extrapolant = :linear,
        controller = :Standard,
        step_limiter! = trivial_limiter!)
```

マルチステップ法。適応的な次数2のL安定固定先頭係数マルチステップBDF法。

### キーワード引数

  * `autodiff`: 自動微分を使用するかどうかを指定するために[ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/)を使用します。自動微分には[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)を使用するか、有限差分には[FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl)を使用します。デフォルトは自動微分のための`AutoForwardDiff()`で、デフォルトでは`chunksize = 0`を使用し、したがって選択のために内部のForwardDiff.jlアルゴリズムを使用します。`FiniteDiff.jl`を使用するには、キーワード引数`fdtype`のデフォルト値が`Val{:forward}()`で、代替として`Val{:central}()`と`Val{:complex}()`を持つ`AutoFiniteDiff()` ADTypeを使用できます。
  * `standardtag`: ForwardDiffのデフォルトの関数固有のタグの代わりにパッケージ固有のタグを使用するかどうかを指定します。詳細については、[このブログ記事](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/)を参照してください。デフォルトは`Val{true}()`です。
  * `concrete_jac`: ヤコビ行列を構築するかどうかを指定します。デフォルトは`nothing`で、これはソルバーの状況に応じて真/偽が選択されることを意味します。たとえば、`linsolve`にKrylov部分空間法が使用されるかどうかです。
  * `linsolve`: 任意の[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)互換の線形ソルバー。たとえば、[KLU.jl](https://github.com/JuliaSparse/KLU.jl)を使用するには、`ABDF2(linsolve = KLUFactorization())`を指定します。`nothing`が渡されると、`DefaultLinearSolver`が使用されます。
  * `precs`: 任意の[LinearSolve.jl互換の前処理器](https://docs.sciml.ai/LinearSolve/stable/basics/Preconditioners/)を左または右の前処理器として使用できます。前処理器は、引数が次のように定義される`Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)`関数によって指定されます。

      * `W`: 非線形系の現在のヤコビ行列。アルゴリズムに応じて、$I - \gamma J$または$I/\gamma - J$として指定されます。これは通常、OrdinaryDiffEq.jlによって定義された`WOperator`型です。これは演算子の遅延表現です。ユーザーは、`convert(AbstractMatrix,W)`を呼び出すことで、`jac_prototype`に一致する`AbstractMatrix`を受け取るためにW行列を必要に応じて構築できます。
      * `du`: 現在のODE導関数
      * `u`: 現在のODE状態
      * `p`: ODEパラメータ
      * `t`: 現在のODE時間
      * `newW`: `W`行列が前回の`precs`呼び出し以降に更新されたかどうかを指定する`Bool`。`newW == true`のときのみ前処理器を更新することを推奨します。
      * `Plprev`: 前の`Pl`。
      * `Prprev`: 前の`Pr`。
      * `solverdata`: ソルバーが`precs`関数に提供できるオプションの追加データ。ソルバー依存であり、変更される可能性があります。

    戻り値は、LinearSolve.jl互換の前処理器のタプル`(Pl,Pr)`です。一方の前処理を指定するには、使用しない前処理器に対して`nothing`を返すだけです。さらに、`precs`はディスパッチを供給する必要があります：

    ```julia
    Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
    ```

    これは、前処理器`(Pl,Pr)`を持つ積分器タイプを構築するためにソルバーセットアップフェーズで使用されます。デフォルトは`precs=DEFAULT_PRECS`で、デフォルトの前処理器関数は次のように定義されています：

    ```julia
    DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
    ```

    /n- `κ`: TBD
  * `tol`: TBD
  * `nlsolve`: TBD
  * `smooth_est`: TBD
  * `extrapolant`: TBD
  * `controller`: TBD
  * `step_limiter!`: 形式`limiter!(u, integrator, p, t)`の関数

## 参考文献

E. Alberdi Celayaa, J. J. Anza Aguirrezabalab, P. Chatzipantelidisc. 適応BDF2式の実装とMATLAB Ode15sとの比較。Procedia Computer Science, 29, pp 1014-1026, 2014. doi: https://doi.org/10.1016/j.procs.2014.05.091
