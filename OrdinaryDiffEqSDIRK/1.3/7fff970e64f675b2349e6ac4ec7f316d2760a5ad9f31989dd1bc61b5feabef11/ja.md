```julia
SFSDIRK7(; chunk_size = Val{0}(),
           autodiff = AutoForwardDiff(),
           standardtag = Val{true}(),
           concrete_jac = nothing,
           diff_type = Val{:forward}(),
           linsolve = nothing,
           precs = DEFAULT_PRECS,
           nlsolve = NLNewton(),
           extrapolant = :linear)
```

SDIRK法。7次の順序の手法。

### キーワード引数

  * `autodiff`: [ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/)を使用して、[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)による自動微分を使用するか、[FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl)による有限差分を使用するかを指定します。デフォルトは自動微分のための`AutoForwardDiff()`で、デフォルトでは`chunksize = 0`を使用し、したがって選択のために内部のForwardDiff.jlアルゴリズムを使用します。`FiniteDiff.jl`を使用するには、`fdtype`というキーワード引数を持つ`AutoFiniteDiff()` ADTypeを使用できます。デフォルト値は`Val{:forward}()`で、代替として`Val{:central}()`と`Val{:complex}()`があります。
  * `standardtag`: ForwardDiffのデフォルトの関数固有のタグの代わりに、パッケージ固有のタグを使用するかどうかを指定します。詳細については、[このブログ記事](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/)を参照してください。デフォルトは`Val{true}()`です。
  * `concrete_jac`: ヤコビ行列を構築するかどうかを指定します。デフォルトは`nothing`で、これはソルバーの状況に応じて真/偽が選択されることを意味します。たとえば、`linsolve`にKrylov部分空間法が使用されるかどうかなどです。
  * `linsolve`: 任意の[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)互換の線形ソルバー。たとえば、[KLU.jl](https://github.com/JuliaSparse/KLU.jl)を使用するには、`SFSDIRK7(linsolve = KLUFactorization())`と指定します。`nothing`が渡されると、`DefaultLinearSolver`が使用されます。
  * `precs`: 任意の[LinearSolve.jl互換の前処理器](https://docs.sciml.ai/LinearSolve/stable/basics/Preconditioners/)を左または右の前処理器として使用できます。前処理器は、`Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)`関数によって指定され、引数は次のように定義されます：

      * `W`: 非線形系の現在のヤコビ行列。アルゴリズムに応じて、$I - \gamma J$または$I/\gamma - J$として指定されます。これは通常、OrdinaryDiffEq.jlによって定義された`WOperator`型です。これは演算子の遅延表現です。ユーザーは、`convert(AbstractMatrix,W)`を呼び出すことで、`jac_prototype`に一致する`AbstractMatrix`を受け取るためにW行列を必要に応じて構築できます。
      * `du`: 現在のODE導関数
      * `u`: 現在のODE状態
      * `p`: ODEパラメータ
      * `t`: 現在のODE時間
      * `newW`: `W`行列が前回の`precs`呼び出し以降に更新されたかどうかを指定する`Bool`。`newW == true`のときのみ前処理器を更新することを推奨します。
      * `Plprev`: 前の`Pl`。
      * `Prprev`: 前の`Pr`。
      * `solverdata`: ソルバーが`precs`関数に渡すことができるオプションの追加データ。ソルバー依存であり、変更される可能性があります。

    戻り値は、LinearSolve.jl互換の前処理器のタプル`(Pl,Pr)`です。一方の前処理を指定するには、使用しない前処理器に対して`nothing`を返すだけです。さらに、`precs`はディスパッチを供給する必要があります：

    ```julia
    Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
    ```

    これは、前処理器`(Pl,Pr)`を持つ積分器タイプを構築するためにソルバーセットアップフェーズで使用されます。デフォルトは`precs=DEFAULT_PRECS`で、デフォルトの前処理器関数は次のように定義されています：

    ```julia
    DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
    ```
  * `nlsolve`: TBD

      * `extrapolant`: TBD

## 参考文献

@article{ferracina2008strong,     title={強い安定性の単一対角暗黙的ルンゲ-クッタ法},     author={Ferracina, Luca and Spijker, MN},     journal={Applied Numerical Mathematics},     volume={58},     number={11},     pages={1675–1686},     year={2008},     publisher={Elsevier}}
