```
hamiltonian_linear(ω1, B1, ω0, T, m0s, R1f, R2f, Rx, R1s, R2s[, dR2sdT2s, dR2sdB1, grad_type])
```

一般化されたBlochモデルの線形近似のハミルトニアンを計算します。

勾配が供給されていない場合、次の順序の次元を持つ6x6（静的）行列を返します `[xf, yf, zf, xs, zs, 1]`；添付された1は、$T_1$緩和をゼロでない熱平衡に許可するための数学的トリックです。勾配が供給されている場合、次の順序の次元を持つ11x11（静的）行列を返します `[xf, yf, zf, xs, zs, dxf/dθ, dyf/dθ, dzf/dθ, dxs/dθ, dzs/dθ,  1]`、ここで `θ` は `grad_type` で指定されたパラメータです。

# 引数

  * `ω1::Real`: Rabi周波数（rad/s単位、y軸周りの回転）
  * `B1::Real`: 正規化された送信B1フィールド、すなわちB1 = 1は適切にキャリブレーションされたB1フィールドに対応
  * `ω0::Real`: Larmor（またはオフ共鳴）周波数（rad/s単位、z軸周りの回転）
  * `T::Real`: 秒単位の時間；これは、例えばRFパルスの持続時間や、`ω1=0`の自由前進の時間である可能性があります
  * `m0s::Real`: 半固体プールの分数サイズ；0から1の範囲であるべき
  * `R1f::Real`: 自由プールの縦緩和率（1/秒単位）
  * `R2f::Real`: 自由プールの横緩和率（1/秒単位）
  * `Rx::Real`: 2つのスピンプール間の交換率（1/秒単位）
  * `R1s::Real`: 半固体プールの縦緩和率（1/秒単位）
  * `R2s::Real`: 半固体プールの横緩和率（1/秒単位）；この数値は、一般化されたBloch論文で説明されている線形近似を実装するために、[`precompute_R2sl`](@ref)によって返される最初の関数で計算できます

オプション：

  * `dR2sdT2s::Real`: 実際のT2sに関する線形化されたR2slの導関数；`grad_type = grad_T2s()`の場合のみ必要；この数値は、[`precompute_R2sl`](@ref)によって返される2番目の関数で計算できます
  * `dR2sdB1::Real`: B1に関する線形化されたR2slの導関数；`grad_type = grad_B1()`の場合のみ必要；この数値は、[`precompute_R2sl`](@ref)によって返される3番目の関数で計算できます
  * `grad_type::grad_param`: `grad_m0s()`, `grad_R1f()`, `grad_R1s()`, `grad_R2f()`, `grad_Rx()`, `grad_T2s()`, `grad_ω0()`, または `grad_B1()`；必要な勾配ごとに1つのハミルトニアンを作成します

# 例

```jldoctest
julia> α = π;

julia> T = 500e-6;

julia> ω1 = α/T;

julia> B1 = 1;

julia> ω0 = 0;

julia> m0s = 0.1;

julia> R1f = 1;

julia> R2f = 15;

julia> Rx = 30;

julia> R1s = 6.5;

julia> R2s = 1e5;

julia> m0 = [0, 0, 1-m0s, 0, m0s, 1];

julia> (xf, yf, zf, xs, zs, _) = exp(hamiltonian_linear(ω1, B1, ω0, T, m0s, R1f, R2f, Rx, R1s, R2s)) * m0
6-element StaticArraysCore.SVector{6, Float64} with indices SOneTo(6):
  0.0010647535813058293
  0.0
 -0.8957848274535014
  0.005126529591877105
  0.08122007142111888
  1.0
```
