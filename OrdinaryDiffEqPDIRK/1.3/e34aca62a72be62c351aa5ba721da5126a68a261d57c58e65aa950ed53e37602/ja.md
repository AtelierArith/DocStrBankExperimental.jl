```julia
PDIRK44(; chunk_size = Val{0}(),
          autodiff = AutoForwardDiff(),
          standardtag = Val{true}(),
          concrete_jac = nothing,
          diff_type = Val{:forward},
          linsolve = nothing,
          precs = DEFAULT_PRECS,
          nlsolve = NLNewton(),
          extrapolant = :constant,
          thread = OrdinaryDiffEq.True())
```

並列対角暗黙ルンゲ-クッタ法。2プロセッサの4次対角非適応暗黙法。

### キーワード引数

  * `autodiff`: [ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/) を使用して、自動微分を [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) 経由で使用するか、有限差分を [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl) 経由で使用するかを指定します。デフォルトは自動微分のための `AutoForwardDiff()` で、デフォルトでは `chunksize = 0` を使用し、したがって選択のために内部の ForwardDiff.jl アルゴリズムを使用します。 `FiniteDiff.jl` を使用するには、キーワード引数 `fdtype` のデフォルト値が `Val{:forward}()` で、代替として `Val{:central}()` と `Val{:complex}()` を持つ `AutoFiniteDiff()` ADType を使用できます。
  * `standardtag`: ForwardDiff のデフォルトの関数固有のタグの代わりに、パッケージ固有のタグを使用するかどうかを指定します。詳細については、[このブログ記事](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/)を参照してください。デフォルトは `Val{true}()` です。
  * `concrete_jac`: ヤコビ行列を構築するかどうかを指定します。デフォルトは `nothing` で、これはソルバーの状況に応じて真/偽が選択されることを意味します。たとえば、`linsolve` に Krylov サブスペース法が使用されるかどうかです。
  * `linsolve`: 任意の [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) 互換の線形ソルバー。たとえば、[KLU.jl](https://github.com/JuliaSparse/KLU.jl) を使用するには、`PDIRK44(linsolve = KLUFactorization())` と指定します。 `nothing` が渡されると、`DefaultLinearSolver` が使用されます。
  * `precs`: 任意の [LinearSolve.jl 互換の前処理器](https://docs.sciml.ai/LinearSolve/stable/basics/Preconditioners/) を左または右の前処理器として使用できます。前処理器は、引数が次のように定義される `Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)` 関数によって指定されます。

      * `W`: 非線形系の現在のヤコビ行列。アルゴリズムに応じて $I - \gamma J$ または $I/\gamma - J$ として指定されます。これは通常、OrdinaryDiffEq.jl によって定義された `WOperator` 型です。これはオペレーターの遅延表現です。ユーザーは `convert(AbstractMatrix,W)` を呼び出すことで、`jac_prototype` に一致する `AbstractMatrix` を受け取るために W 行列を必要に応じて構築できます。
      * `du`: 現在の ODE の導関数
      * `u`: 現在の ODE の状態
      * `p`: ODE のパラメータ
      * `t`: 現在の ODE の時間
      * `newW`: `W` 行列が前回の `precs` 呼び出し以降に更新されたかどうかを指定する `Bool`。 `newW == true` のときのみ前処理器を更新することを推奨します。
      * `Plprev`: 前の `Pl`。
      * `Prprev`: 前の `Pr`。
      * `solverdata`: ソルバーが `precs` 関数に提供できるオプションの追加データ。ソルバー依存であり、変更される可能性があります。

    戻り値は、LinearSolve.jl 互換の前処理器のタプル `(Pl,Pr)` です。一方の前処理を指定するには、使用しない前処理器に対して `nothing` を返すだけです。さらに、`precs` はディスパッチを供給する必要があります：

    ```julia
    Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
    ```

    これは、前処理器 `(Pl,Pr)` で積分器タイプを構築するためにソルバーセットアップフェーズで使用されます。デフォルトは `precs=DEFAULT_PRECS` で、デフォルトの前処理器関数は次のように定義されています：

    ```julia
    DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
    ```
  * `nlsolve`: TBD,
  * `extrapolant`: TBD,
  * `thread`: Julia が複数のスレッドで起動されたときに、適切な CPU 配列での内部ブロードキャストを直列 (`thread = OrdinaryDiffEq.False()`) にするか、複数のスレッドを使用するか (`thread = OrdinaryDiffEq.True()`) を決定します。

## 参考文献

"@article{iserles1990theory, title={On the theory of parallel Runge—Kutta methods}, author={Iserles, Arieh and Norrsett, SP}, journal={IMA Journal of numerical Analysis}, volume={10}, number={4}, pages={463–488}, year={1990}, publisher={Oxford University Press}}
