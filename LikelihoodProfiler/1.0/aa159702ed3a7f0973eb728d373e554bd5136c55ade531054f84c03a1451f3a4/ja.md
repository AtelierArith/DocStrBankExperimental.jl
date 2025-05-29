```
profile(plprob::PLProblem, method::AbstractProfilerMethod; 
        idxs::AbstractVector{<:Int} = eachindex(get_optpars(plprob)),
        parallel_type::Symbol=:none, kwargs...)
```

指定されたプロファイリング `method` を使用して、与えられた問題 `plprob` の尤度関数をプロファイルします。

### 引数

  * `plprob::PLProblem{ParameterProfile}`: プロファイルされるパラメータと尤度関数を含むプロファイリング問題のインスタンス。
  * `method::AbstractProfilerMethod`: プロファイリングに使用されるメソッド。
  * `idxs::AbstractVector{<:Int}`: プロファイルされるパラメータのインデックス。デフォルトはすべてのパラメータ。
  * `parallel_type::Symbol`: 使用される並列処理のタイプを指定します。デフォルトは `:none`。
  * `maxiters::Int`: プロファイリングプロセスの1つのブランチ（左と右）の最大反復回数。デフォルトは `1e4`。
  * `verbose::Bool`: プロファイリングプロセスの進行状況を表示するかどうかを示します。デフォルトは `false`。

### 戻り値

  * プロファイリング結果 `PLSolution` を返します。

### 例

```julia
plprob = PLProblem(optprob, optpars, [(-10.,10.), (-5.,5.)])
method = OptimizationProfiler(optimizer = Optimization.LBFGS(), stepper = FixedStep())
sol = profile(plprob, method; idxs=[1])
```
