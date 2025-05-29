```
Spin([M], M0, T1, T2, Δf, [pos]) <: AbstractSpin
```

単一スピンを表すオブジェクトを作成します。

# プロパティ

  * `M::Magnetization = Magnetization(0, 0, M0)`: 磁化ベクトル
  * `M0::Real`: 平衡磁化
  * `T1::Real`: スピン-格子回復時間定数 (ms)
  * `T2::Real`: スピン-スピン回復時間定数 (ms)
  * `Δf::Real`: オフ共鳴周波数 (Hz)
  * `pos::Position = Position(0, 0, 0)`: 空間的位置 (cm)
  * `N::Int = 1`: コンパートメントの数

# 例

```jldoctest
julia> Spin(1, 1000, 100, 0, Position(1, 2, 3))
Spin{Float64}:
 M = Magnetization(0.0, 0.0, 1.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(1.0, 2.0, 3.0) cm

julia> Spin(Magnetization(1, 2, 3), 1, 1000, 100, 0)
Spin{Float64}:
 M = Magnetization(1.0, 2.0, 3.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(0.0, 0.0, 0.0) cm
```
