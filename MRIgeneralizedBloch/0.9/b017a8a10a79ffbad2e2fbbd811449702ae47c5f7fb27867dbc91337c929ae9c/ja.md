```
apply_hamiltonian_sled!(∂m∂t, m, p, t)
```

Sledのハミルトニアンを`m`に適用し、結果として得られる時間に関する導関数を`∂m∂t`に書き込みます。

# 引数

  * `∂m∂t::Vector{<:Real}`: 時間に関する`m`の導関数を記述する長さ1のベクトル。このベクトルは任意の値を含むことができ、`H * m`で置き換えられます。
  * `m::Vector{<:Real}`: `zs`の磁化を記述する長さ1のベクトル。
  * `p::NTuple{6 or 10, Any}`: 孤立した半固体プールをシミュレーションするための`(ω1, B1, ω0, R1s, T2s, g)`または結合スピンシステムをシミュレーションするための`(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g)`; ここで

      * `ω1::Real`: ラビ周波数（y軸まわりの回転）を表すrad/sまたは
      * `ω1(t)::Function`: 形状付きRFパルスの時間の関数としてのラビ周波数を表すrad/s
      * `B1::Real`: `B1=1`が完全にキャリブレーションされたRFフィールドに対応するように正規化されたB1スケーリング
      * `ω0::Real`: ラーモア周波数またはオフ共鳴周波数を表すrad/s（自由スピンプールにのみ使用される）
      * `R1f::Real`: 自由プールの縦方向スピン緩和率（1/秒）
      * `R2f::Real`: 自由プールの横方向スピン緩和率（1/秒）
      * `R1s::Real`: 半固体の縦方向スピン緩和率（1/秒）
      * `Rx::Real`: 2つのプール間の交換率（1/秒）
      * `T2s::Real`: 横方向スピン緩和時間（秒）
      * `g::Function`: 形式`G(κ) = G((t-τ)/T2s)`のグリーン関数
  * `t::Real`: 時間（秒）

# 例

```jldoctest
julia> using DifferentialEquations


julia> α = π/2;

julia> TRF = 100e-6;

julia> ω1 = α/TRF;

julia> B1 = 1;

julia> ω0 = 0;

julia> R1s = 2;

julia> T2s = 10e-6;

julia> G = interpolate_greens_function(greens_superlorentzian, 0, TRF / T2s);

julia> m0 = [1];

julia> sol = solve(ODEProblem(apply_hamiltonian_sled!, m0, (0, TRF), (ω1, 1, ω0, R1s, T2s, G)), Tsit5())
retcode: Success
Interpolation: specialized 4th order "free" interpolation
t: 3-element Vector{Float64}:
 0.0
 7.475414666720001e-5
 0.0001
u: 3-element Vector{Vector{Float64}}:
 [1.0]
 [0.6313928231811967]
 [0.4895365449661915]

julia> using Plots

julia> plot(sol, labels=["zs"], xlabel="t (s)", ylabel="m(t)");



```
