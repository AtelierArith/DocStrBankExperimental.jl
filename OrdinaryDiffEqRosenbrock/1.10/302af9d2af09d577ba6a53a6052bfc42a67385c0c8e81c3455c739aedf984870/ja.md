```julia
ROS2(; - `standardtag`: パッケージ固有のタグを使用するかどうかを指定します
           ForwardDiffのデフォルトの関数固有のタグの代わりに。詳細については、
           [このブログ記事](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/)を参照してください。
           デフォルトは`Val{true}()`です。
       - `autodiff`: [ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/)を使用して、
           [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl)を介して自動微分を使用するか、
           [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl)を介して有限差分を使用するかを指定します。
           自動微分の場合、デフォルトは`AutoForwardDiff()`で、デフォルトでは
           `chunksize = 0`を使用し、したがって選択のために内部のForwardDiff.jlアルゴリズムを使用します。
           `FiniteDiff.jl`を使用するには、`AutoFiniteDiff()` ADTypeを使用でき、
           これはデフォルト値`Val{:forward}()`を持つキーワード引数`fdtype`を持ち、
           代替として`Val{:central}()`と`Val{:complex}()`があります。
       - `concrete_jac`: ヤコビ行列を構築するかどうかを指定します。デフォルトは
           `nothing`で、これはソルバーの状況に応じて真/偽が選択されることを意味します
           例えば、`linsolve`にKrylov部分空間法が使用されるかどうかなど。
       - `linsolve`: 任意の[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)互換の線形ソルバー。
         例えば、[KLU.jl](https://github.com/JuliaSparse/KLU.jl)を使用するには、
         `ROS2(linsolve = KLUFactorization())`を指定します。
          `nothing`が渡されると、`DefaultLinearSolver`が使用されます。
       - `precs`: 任意の[LinearSolve.jl互換の前処理器](https://docs.sciml.ai/LinearSolve/stable/basics/Preconditioners/)
         を左または右の前処理器として使用できます。
         前処理器は、`Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)`
         関数によって指定され、引数は次のように定義されます：
           - `W`: 非線形システムの現在のヤコビ行列。アルゴリズムに応じて
               ``I - \gamma J``または``I/\gamma - J``として指定されます。これは
               OrdinaryDiffEq.jlによって定義された`WOperator`型であることが一般的です。これは
               演算子の遅延表現です。ユーザーは`convert(AbstractMatrix,W)`を呼び出すことで
               `jac_prototype`に一致する`AbstractMatrix`を受け取るためにW行列を必要に応じて構築できます。
           - `du`: 現在のODE導関数
           - `u`: 現在のODE状態
           - `p`: ODEパラメータ
           - `t`: 現在のODE時間
           - `newW`: `W`行列が前回の`precs`呼び出し以降に更新されたかどうかを指定する`Bool`。
               `newW == true`のときのみ前処理器を更新することを推奨します。
           - `Plprev`: 前の`Pl`。
           - `Prprev`: 前の`Pr`。
           - `solverdata`: ソルバーが`precs`関数に渡すことができるオプションの追加データ。
               ソルバー依存であり、変更される可能性があります。
         戻り値は、LinearSolve.jl互換の前処理器のタプル`(Pl,Pr)`です。
         一方の前処理を指定するには、使用されない前処理器に対して`nothing`を返すだけです。
         さらに、`precs`はディスパッチを供給する必要があります：
         ```julia
         Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
         ```
         これはソルバーのセットアップフェーズで使用され、前処理器`(Pl,Pr)`を持つ
         積分器タイプを構築します。
         デフォルトは`precs=DEFAULT_PRECS`で、デフォルトの前処理器関数は次のように定義されています：
         ```julia
         DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
         ```)
```

ロゼンブロック-ワナー法。内部ステージが2つある2次のL安定ロゼンブロック法です。

### キーワード引数

  * `chunk_size`: TBD
  * `standardtag`: TBD
  * `autodiff`: ヤコビ行列をADを介して計算するかどうかを制御するブール値
  * `concrete_jac`: 形式`jac!(J, u, p, t)`の関数
  * `diff_type`: TBD
  * `linsolve`: 内部線形システムのカスタムソルバー
  * `precs`: 内部線形ソルバーのカスタム前処理器

## 参考文献

  * J. G. Verwer et al. (1999): 光化学拡散問題に適用された2次ロゼンブロック法 https://doi.org/10.1137/S1064827597326651
