```
computeEigenvalues(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    guess::T;
    nls_xtol::Real = convert(T, 1.0e-10),
    nls_ftol::Real = convert(T, 1.0e-10),
    nls_iterations::Int = 1000
    ) where {N <: Unsigned, T <: Complex}
```

問題 `p` に対して対応するキャッシュ `c` の単一の固有値を計算します。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::NumericAIMProblem`: 以前に定義された問題データ。
  * `c::AIMCache`: p から構築されたキャッシュ。
  * `nls_xtol::Real`: 収束が宣言される二つの連続した反復間の x のノルム差。
  * `nls_ftol::Real`: 収束が宣言される残差の無限ノルム。
  * `nls_iterations::Int`: NLsolve によって実行される最大反復回数。

# 出力

`nlsolve` によって返される `SolverResults` 型のオブジェクト。詳細については [NLsolve.jl](https://github.com/JuliaNLSolvers/NLsolve.jl) を参照してください。
