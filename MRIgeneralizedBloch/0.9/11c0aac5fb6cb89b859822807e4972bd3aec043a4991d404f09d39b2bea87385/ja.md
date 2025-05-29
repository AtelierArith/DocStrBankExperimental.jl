```
apply_hamiltonian_gbloch!(∂m∂t, m, mfun, p, t)
```

一般化されたブロッホハミルトニアンを `m` に適用し、結果として得られる時間に関する導関数を `∂m∂t` に書き込みます。

# 引数

  * `∂m∂t::Vector{Real}`: 時間に関する `m` の導関数を記述するベクトル。このベクトルは `m` と同じサイズでなければならず、任意の値を含むことができ、`H * m` に置き換えられます。
  * `m::Vector{Real}`: スピンアンサンブル状態のベクトルで、勾配が計算されていない場合は `[xf, yf, zf, zs, 1]` の形を持ち、`θn` に関する n 個の導関数が計算される場合は `[xf, yf, zf, zs, 1, ∂xf/∂θ1, ∂yf/∂θ1, ∂zf/∂θ1, ∂zs/∂θ1, 0, ..., ∂xf/∂θn, ∂yf/∂θn, ∂zf/∂θn, ∂zs/∂θn, 0]` の形を持ちます。
  * `mfun`: ヒストリ関数。`mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5n + 5)` で初期化でき、n 個の勾配に対して、遅延微分方程式ソルバーによって更新されます。
  * `p::NTuple{6,Any}`: `(ω1, B1, ω0, R1s, T2s, g)` または
  * `p::NTuple{6,Any}`: `(ω1, B1,  φ, R1s, T2s, g)` または
  * `p::NTuple{10,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g)` または
  * `p::NTuple{10,Any}`: `(ω1, B1,  φ, m0s, R1f, R2f, Rx, R1s, T2s, g)` または
  * `p::NTuple{12,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g, dG_o_dT2s_x_T2s, grad_list)` または
  * `p::NTuple{12,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g, dG_o_dT2s_x_T2s, grad_list)` で、以下のエントリを持ちます。

      * `ω1::Real`: ラビ周波数（y軸まわりの回転）を rad/s で表したもの。
      * `ω1(t)::Function`: 形状付き RF パルスの時間の関数としてのラビ周波数を rad/s で表したもの。
      * `B1::Real`: `B1=1` が完全にキャリブレーションされた RF フィールドに対応するように正規化された B1 スケーリング。
      * `ω0::Real`: ラーモア周波数またはオフ共鳴周波数を rad/s で表したもの。
      * `φ::Function`: 周波数/位相スイープパルスの時間の関数としての RF 位相を rad で表したもの（`ω1(t)::Function` と組み合わせてのみ機能します）。
      * `m0s::Real`: 0 から 1 の範囲の分数半固体スピンプールサイズ。
      * `R1f::Real`: 自由プールの縦スピン緩和率を 1/秒で表したもの。
      * `R2f::Real`: 自由プールの横スピン緩和率を 1/秒で表したもの。
      * `Rx::Real`: 2 つのプール間の交換率を 1/秒で表したもの。
      * `R1s::Real`: 半固体プールの縦スピン緩和率を 1/秒で表したもの。
      * `T2s::Real`: 半固体プールの横スピン緩和時間を秒で表したもの。
      * `g::Function`: 形式 `G(κ) = G((t-τ)/T2s)` のグリーン関数。
      * `dG_o_dT2s_x_T2s::Function`: T2s に関するグリーン関数の導関数で、T2s で乗算される。形式 `dG_o_dT2s_x_T2s(κ) = dG_o_dT2s_x_T2s((t-τ)/T2s)`。
      * `grad_list::Vector{grad_param}`: 計算される勾配のリスト。すなわち、`[grad_m0s(), grad_R1f(), grad_R2f(), grad_Rx(), grad_R1s(), grad_T2s(), grad_ω0(), grad_B1()]` の任意の部分集合。ベクトルの長さは n でなければならず（引数 `m` と `∂m∂t` を参照）、見かけの `R1a = R1f = R1s` に関する導関数は `grad_R1a()` で計算できます。
  * `t::Real`: 時間を秒で表したもの。

オプション:

  * `pulsetype=:normal`: 通常の RF パルスのデフォルトを使用します。オプション `pulsetype=:inversion` は、半固体プールの飽和とその導関数を計算するためのものであるため、注意して扱う必要があります。

# 例

```jldoctest
julia> using DifferentialEquations


julia> α = π/2;

julia> TRF = 100e-6;

julia> ω1 = α/TRF;

julia> B1 = 1;

julia> ω0 = 0;

julia> m0s = 0.2;

julia> R1f = 1/3;

julia> R2f = 15;

julia> R1s = 2;

julia> T2s = 10e-6;

julia> Rx = 30;

julia> G = interpolate_greens_function(greens_superlorentzian, 0, TRF / T2s);


julia> m0 = [0; 0; 1-m0s; m0s; 1];

julia> mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5);

julia> sol = solve(DDEProblem(apply_hamiltonian_gbloch!, m0, mfun, (0, TRF), (ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, G)))
retcode: Success
Interpolation: specialized 4th order "free" interpolation, specialized 2nd order "free" stiffness-aware interpolation
t: 9-element Vector{Float64}:
 0.0
 1.375006182301112e-7
 1.512506800531223e-6
 8.042561696923577e-6
 2.107848894861101e-5
 3.9114182159866e-5
 6.26879358261189e-5
 9.147711414688425e-5
 0.0001
u: 9-element Vector{Vector{Float64}}:
 [0.0, 0.0, 0.8, 0.2, 1.0]
 [0.0017278806030763402, 0.0, 0.7999981340131751, 0.19999953350448, 1.0]
 [0.019004717382235078, 0.0, 0.7997742277135814, 0.19994357804868362, 1.0]
 [0.10079111348917136, 0.0, 0.7936248122939504, 0.19842287240368398, 1.0]
 [0.2600257867257624, 0.0, 0.7565529666157949, 0.1898191304278861, 1.0]
 [0.46104237829774064, 0.0, 0.6537239462232086, 0.16937683398576228, 1.0]
 [0.6661740376622253, 0.0, 0.44261209248221817, 0.13589311206074786, 1.0]
 [0.7923117772809817, 0.0, 0.10713073823030607, 0.09390260581965477, 1.0]
 [0.7994211188442756, 0.0, 0.0004403374305009168, 0.08214809659226184, 1.0]

julia> using Plots

julia> plot(sol, labels=["xf" "yf" "zf" "zs" "1"], xlabel="t (s)", ylabel="m(t)");




julia> dG_o_dT2s_x_T2s = interpolate_greens_function(dG_o_dT2s_x_T2s_superlorentzian, 0, TRF / T2s);


julia> grad_list = (grad_R2f(), grad_m0s());


julia> m0 = [0; 0; 1-m0s; m0s; 1; zeros(5*length(grad_list))];


julia> mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5 + 5*length(grad_list));

julia> sol = solve(DDEProblem(apply_hamiltonian_gbloch!, m0, mfun, (0, TRF), (ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, G, dG_o_dT2s_x_T2s, grad_list)));




julia> plot(sol);


```
