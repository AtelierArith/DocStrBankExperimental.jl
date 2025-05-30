```julia
SFSDIRK8(; chunk_size = Val{0}(),
           autodiff = AutoForwardDiff(),
           standardtag = Val{true}(),
           concrete_jac = nothing,
           diff_type = Val{:forward}(),
           linsolve = nothing,
           precs = DEFAULT_PRECS,
           nlsolve = NLNewton(),
           extrapolant = :linear)
```

SDIRK法。8次の順序の方法。

### キーワード引数

  * `autodiff`: 自動微分を使用するかどうかを指定するために [ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/) を使用します。自動微分には [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) を、有限差分には [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl) を使用します。デフォルトでは自動微分のために `AutoForwardDiff()` が使用され、デフォルトで `chunksize = 0` を使用し、したがって選択のために内部の ForwardDiff.jl アルゴリズムを使用します。 `FiniteDiff.jl` を使用するには、キーワード引数 `fdtype` のデフォルト値が `Val{:forward}()` で、代替として `Val{:central}()` と `Val{:complex}()` を持つ `AutoFiniteDiff()` ADType を使用できます。
  * `standardtag`: ForwardDiff のデフォルトの関数固有のタグの代わりに、パッケージ固有のタグを使用するかどうかを指定します。詳細については、[このブログ記事](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/)を参照してください。デフォルトは `Val{true}()` です。
  * `concrete_jac`: ヤコビ行列を構築するかどうかを指定します。デフォルトは `nothing` で、これはソルバーの状況に応じて真/偽が選択されることを意味します。たとえば、`linsolve` に Krylov サブスペース法が使用されるかどうかなどです。
  * `linsolve`: 任意の [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) 互換の線形ソルバー。たとえば、[KLU.jl](https://github.com/JuliaSparse/KLU.jl) を使用するには、`SFSDIRK8(linsolve = KLUFactorization())` と指定します。 `nothing` が渡されると、`DefaultLinearSolver` が使用されます。
  * `precs`: 任意の [LinearSolve.jl] 互換の前処理器を左または右の前処理器として使用できます。前処理器は、引数が次のように定義される `Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)` 関数によって指定されます。

      * `W`: 非線形系の現在のヤコビ行列。アルゴリズムに応じて $I - \gamma J$ または $I/\gamma - J$ として指定されます。これは通常、OrdinaryDiffEq.jl によって定義された `WOperator` 型です。これはオペレーターの遅延表現です。ユーザーは `convert(AbstractMatrix,W)` を呼び出すことで、`jac_prototype` に一致する `AbstractMatrix` を受け取るために W 行列を必要に応じて構築できます。
      * `du`: 現在の ODE の導関数
      * `u`: 現在の ODE の状態
      * `p`: ODE のパラメータ
      * `t`: 現在の ODE の時間
      * `newW`: `W` 行列が前回の `precs` 呼び出し以降に更新されたかどうかを指定する `Bool`。 `newW == true` のときのみ前処理器を更新することを推奨します。
      * `Plprev`: 前の `Pl`。
      * `Prprev`: 前の `Pr`。
      * `solverdata`: ソルバーが `precs` 関数に渡すことができるオプションの追加データ。ソルバー依存であり、変更される可能性があります。

    戻り値は、LinearSolve.jl 互換の前処理器のタプル `(Pl,Pr)` です。一方の前処理を指定するには、使用しない前処理器に対して `nothing` を返すだけです。さらに、`precs` はディスパッチを供給する必要があります：

    ```julia
    Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
    ```

    これは、前処理器 `(Pl,Pr)` で積分器タイプを構築するためにソルバーセットアップフェーズで使用されます。デフォルトは `precs=DEFAULT_PRECS` で、デフォルトの前処理器関数は次のように定義されています：

    ```julia
    DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
    ```
  * `nlsolve`: TBD

      * `extrapolant`: TBD

## 参考文献

@article{ferracina2008strong,     title={強い安定性の単一対角暗黙的ルンゲ-クッタ法},     author={Ferracina, Luca and Spijker, MN},     journal={Applied Numerical Mathematics},     volume={58},     number={11},     pages={1675–1686},     year={2008},     publisher={Elsevier}}
