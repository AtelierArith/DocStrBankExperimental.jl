```
solve(problem::PDMPProblem, algo; verbose = false, n_jumps = Inf64, save_positions = (false, true), reltol = 1e-7, abstol = 1e-9, save_rate = false, finalizer = finalize_dummy, kwargs...)
```

PDMP `problem`をCHVアルゴリズムを使用してシミュレートします。

# 引数

  * `problem::PDMPProblem`
  * `alg`は`CHV(ode)`（[CHVアルゴリズム](https://arxiv.org/abs/1504.06873)用）、`Rejection(ode)`は拒否アルゴリズム用、`RejectionExact()`はジャンプ間の流れが解析的に知られている場合の拒否アルゴリズム用です。この後者の場合、`prob.F`が流れの仕様に使用されます。ODEソルバー`ode`は、例えば`Tsit5()`のような[DifferentialEquations.jl](https://github.com/JuliaDiffEq/DifferentialEquations.jl)の任意のソルバーであることができます。また、リスト`[:cvode, :lsoda, :adams, :BDF, :euler]`のいずれかでも構いません。実際、このパッケージはイテレータインターフェースを実装しており、`ode = LSODA()`ではまだ機能しません。ODEソルバー`LSODA()`にアクセスするには、`ode = :lsoda`を使用する必要があります。
  * `verbose`はシミュレーション中に情報を表示します
  * `n_jumps`は計算される最大ジャンプ数です
  * `save_positions`は記録するジャンプ位置を指定します。前ジャンプ（save*positions[1] = true）および/または後ジャンプ（save*positions[2] = true）。
  * `reltol`: ODEソルバーで使用される相対許容誤差
  * `abstol`: ODEソルバーで使用される絶対許容誤差
  * `ind_save_c`: `xc`のどのインデックスを保存するか
  * `ind_save_d`: `xd`のどのインデックスを保存するか
  * `save_rate = true`: ソルバーに総レートを保存させる必要があります。これは、拒否アルゴリズムを第二の試みとして使用するためにレートの境界を推定する際に役立ちます。
  * `X_extended = zeros(Tc, 1 + 1)`: （高度な使用）[CHVアルゴリズム](https://arxiv.org/abs/1504.06873)で拡張配列の形状を提供するために使用されるオプションです。例えば`StaticArrays.jl`を使用する際に役立ちます。
  * `finalizer = finalize_dummy`: ユーザーが各ジャンプ後に呼び出される関数`finalizer(rate, xc, xd, p, t)`を渡すことを可能にします。保存/プロットメカニズムをオーバーロード/追加するために使用できます。
  * `kwargs`はODEソルバーに渡されるキーワード引数（DifferentialEquations.jlから）

!!! note "`JumpProcesses`ラッパーのためのソルバー"
    `VariableJumps`に対して機能する基本的なラッパーを提供します（他のタイプのジャンプは十分にテストされていません）。このタイプの問題には`CHV`を使用できます。`Rejection`ソルバーはまだ機能していません。

