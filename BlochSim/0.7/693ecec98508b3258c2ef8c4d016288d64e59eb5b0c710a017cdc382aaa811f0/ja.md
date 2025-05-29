```
SpinMC([M], M0, frac, T1, T2, Δf, τ, [pos]) <: AbstractSpin
```

複数のコンパートメントを持つ単一スピンを表すオブジェクトを作成します。

# プロパティ

  * `M::MagnetizationMC = Meq`: 磁化ベクトル
  * `Meq::MagnetizationMC = MagnetizationMC((0, 0, frac[1] * M0), ...)`: 平衡磁化ベクトル
  * `M0::Real`: 平衡磁化
  * `frac::Tuple{<:Real}`: 各コンパートメントの水分率
  * `T1::Tuple{<:Real}`: スピン-格子回復時間定数 (ms)
  * `T2::Tuple{<:Real}`: スピン-スピン回復時間定数 (ms)
  * `Δf::Tuple{<:Real}`: オフ共鳴周波数 (Hz)
  * `r::Tuple{Tuple{<:Real}}`: 交換率 (1/ms); `r[i][j]` はコンパートメント `i` からコンパートメント `j` への交換率
  * `pos::Position = Position(0, 0, 0)`: 空間的位置 (cm)
  * `N::Int = length(frac)`: コンパートメントの数

## 注意

`SpinMC` コンストラクタは `τ` (逆交換率、または滞在時間) を入力として受け取り、*r* ではありません。さらに、`τ` は `N^2 - N` 要素を持つ `Tuple` として与えられ、(τ12, τ13, ..., τ1N, τ21, τ23, ..., τ2N, ...) のように配置されます。

# 例

```jldoctest
julia> SpinMC(1, (0.2, 0.8), (400, 1000), (20, 100), (15, 0), (100, 25))
SpinMC{Float64,2}:
 M = MagnetizationMC((0.0, 0.0, 0.2), (0.0, 0.0, 0.8))
 M0 = 1.0
 frac = (0.2, 0.8)
 T1 = (400.0, 1000.0) ms
 T2 = (20.0, 100.0) ms
 Δf = (15.0, 0.0) Hz
 r = ((0.0, 0.01), (0.04, 0.0)) 1/ms
 pos = Position(0.0, 0.0, 0.0) cm
```
