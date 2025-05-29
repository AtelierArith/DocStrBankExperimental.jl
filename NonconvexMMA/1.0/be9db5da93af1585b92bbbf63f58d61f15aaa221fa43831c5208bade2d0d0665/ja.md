```
MMAOptions
```

MMAアルゴリズムのすべてのオプションを格納する構造体です。`MMAOptions`のフィールドは以下の通りです：

  * `maxiter`: 内部反復の最大数。`MMA87`では、外部反復ごとに1回の内部反復があります。
  * `outer_maxiter`: 外部反復の最大数。
  * `maxinner`: [`MMA02`](@ref)の外部反復ごとの内部反復の最大数。[`MMA87`](@ref)には適用されません。
  * `tol`: [`Tolerance`](@ref)型の許容誤差構造体。
  * `s_init`: 元の[`MMA02`](@ref)論文で定義されています。
  * `s_incr`: 元の[`MMA02`](@ref)論文で定義されています。
  * `s_decr`: 元の[`MMA02`](@ref)論文で定義されています。
  * `store_trace`: trueの場合、トレースが保存されます。
  * `dual_options`: [`Optim.jl`](https://github.com/JuliaNLSolvers/Optim.jl)から双対最適化器に渡されるオプション。
  * `convcriteria`: MMAアルゴリズムの収束基準を指定する[`ConvergenceCriteria`](@ref)のインスタンス。
  * `verbose`: true/false、trueの場合は収束統計を出力します。
