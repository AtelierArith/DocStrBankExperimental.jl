```
Options(; metaprogramming::Bool = true, μ::Real = 1, ϵ::Real = eps(), A_init_value::Real = 1.0, A_lower::Union{Real, Nothing} = nothing, A_upper::Union{Real, Nothing} = nothing, A_use_sobol::Bool = false, V_init_value::Real = 1.0, V_lower::Union{Real, Nothing} = nothing, V_upper::Union{Real, Nothing} = nothing, V_use_sobol::Bool = false, low = -1e10, high = 1e10, tol = 1e-10, maxiter = 1e6)
```

最適化と微積分に使用されるさまざまなパラメータを構成するための構造体 `Options` を定義します。メタプログラミング、初期値、最適化の境界、および二分探索の制御に対して柔軟なデフォルトを提供します。

# フィールド

  * `metaprogramming::Bool`: シンボリック微分変換のためのメタプログラミングを有効にします。デフォルトは `true` です。
  * `μ::Real`: 正則化ハイパーパラメータ。デフォルトは `1` です。
  * `ϵ::Real`: 正則化ハイパーパラメータ。デフォルトは `eps()` です。
  * `A_init_value::Real`: パラメータ `A` の初期値。デフォルトは `1.0` です。
  * `A_lower::Union{Real, Nothing}`: `A` の下限、または `nothing`。デフォルトは `nothing` です。
  * `A_upper::Union{Real, Nothing}`: `A` の上限、または `nothing`。デフォルトは `nothing` です。
  * `A_use_sobol::Bool`: `A` の初期化にSobol列を使用します。デフォルトは `false` です。
  * `V_init_value::Real`: パラメータ `V` の初期値。デフォルトは `1.0` です。
  * `V_lower::Union{Real, Nothing}`: `V` の下限、または `nothing`。デフォルトは `nothing` です。
  * `V_upper::Union{Real, Nothing}`: `V` の上限、または `nothing`。デフォルトは `nothing` です。
  * `V_use_sobol::Bool`: `V` の初期化にSobol列を使用します。デフォルトは `false` です。
  * `low::Real`: 二分探索の下限。デフォルトは `-1e10` です。
  * `high::Real`: 二分探索の上限。デフォルトは `1e10` です。
  * `tol::Real`: 二分探索を停止するための許容誤差。デフォルトは `1e-10` です。
  * `maxiter::Real`: 二分探索の最大反復回数。デフォルトは `1e6` です。

!!! info
    `metaprogramming` フラグは、シンボリック微分変換中にメタプログラミングが使用されるかどうかを制御します。Symbolics.jl の原子と基本的な Julia との間の変換は、これなしでも行うことができますが、このアプローチは遅く、より多くの呼び出しを必要とします。それにもかかわらず、このフラグは、パイプラインでメタプログラミングを避けたいユーザーのために提供されています。

