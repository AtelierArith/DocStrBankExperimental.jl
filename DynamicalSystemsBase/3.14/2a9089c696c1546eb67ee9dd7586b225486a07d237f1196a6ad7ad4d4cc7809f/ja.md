```
TangentDynamicalSystem <: DynamicalSystem
TangentDynamicalSystem(ds::CoreDynamicalSystem; kwargs...)
```

`ds`（[`CoreDynamicalSystem`](@ref)である必要があります）の進化と、*接空間における動力学*（線形化された動力学または接動力学とも呼ばれる）に従って進化する`k`の偏差ベクトルを束ねる動的システムです。

`TangentDynamicalSystem`のために、`ds`の状態は**必ず**`AbstractVector`でなければなりません。

`TangentDynamicalSystem`は、以下の調整を加えた[`DynamicalSystem`](@ref)インターフェースに従います：

  * `reinit!`は追加のキーワード`Q0`を取ります（デフォルトは以下と同じ）。
  * 偏差ベクトルのために、追加の関数[`current_deviations`](@ref)と[`set_deviations!`](@ref)が提供されます。

## キーワード引数

  * `k`または`Q0`：`Q0`は初期偏差ベクトルを表します（各列 = 1ベクトル）。`k::Int`が与えられた場合、単位行列の最初の`k`列を持つ行列`Q0`が作成されます。そうでない場合、`Q0`は行列として直接与えることができます。`size(Q, 1) == dimension(ds)`が成り立つ必要があります。ランダムな直交ベクトルには[`orthonormal`](@ref)を使用できます。デフォルトでは`k = dimension(ds)`が使用されます。
  * `u0 = current_state(ds)`：開始状態。
  * `J`および`J0`：以下の「ヤコビ行列」セクションを参照してください。

## 説明

$$
u
$$

を`ds`の状態、$y$を偏差（または摂動）ベクトルとします。これら二つは次のように並行して進化します。

$$
\begin{array}{rcl}
\frac{d\vec{x}}{dt} &=& f(\vec{x}) \\
\frac{dY}{dt} &=& J_f(\vec{x}) \cdot Y
\end{array}
\quad \mathrm{または}\quad
\begin{array}{rcl}
\vec{x}_{n+1} &=& f(\vec{x}_n) \\
Y_{n+1} &=& J_f(\vec{x}_n) \cdot Y_n.
\end{array}
$$

連続時間または離散時間にそれぞれ対応します。ここで、$f$は[`dynamic_rule`](@ref)`(ds)`であり、$J_f$は$f$のヤコビ行列です。

## ヤコビ行列

キーワード`J`はヤコビ行列関数を提供します。これは`f`、すなわち[`dynamic_rule`](@ref)と同じ形式のJulia関数でなければなりません。具体的には、`J(u, p, n) -> M::SMatrix`はアウトオブプレースバージョン、または`J(M, u, p, n)`はインプレースバージョンで、`M`に対してインプレースで作用します。いずれの場合も、`M`は偏差ベクトルの進化に使用されるヤコビ行列です。

デフォルトでは`J = nothing`です。この場合、`J`はモジュール[`ForwardDiff`](https://github.com/JuliaDiff/ForwardDiff.jl)を使用して自動的に構築されるため、その制限もここに適用されます。`ForwardDiff`は非常に高速ですが、正確なシステムによっては手動でコーディングされたヤコビ行列を提供することで大幅な速度向上が得られる可能性があるため、推奨されます。さらに、自動およびインプレースのヤコビ行列は時間依存であってはなりません。

キーワード`J0`は初期化されたヤコビ行列`J0`を渡すことを可能にします。これは、時間進化中にヤコビ行列の一部の成分のみが変化する大規模なインプレースシステムに便利です。`J0`は疎行列または他の任意の行列型であることができます。与えられない場合、ゼロの行列が使用されます。`J0`はアウトオブプレースシステムでは無視されます。 ```
