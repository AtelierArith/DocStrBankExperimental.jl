```
freeprecess(t, M0, T1, T2, Δf)
```

自由前進をシミュレートします。すなわち、リラクゼーションとオフ共鳴前進です。`A * M + B` の形で、磁化 `M` に自由前進を適用する `(A, B)` を返します。

インプレースバージョンについては、[`freeprecess!`](@ref)を参照してください。

# 引数

  * `t::Real`: 自由前進の期間 (ms)
  * `M0::Real`: 平衡磁化
  * `T1::Real`: スピン-格子回復時間定数 (ms)
  * `T2::Real`: スピン-スピン回復時間定数 (ms)
  * `Δf::Real`: オフ共鳴周波数 (Hz)

# 例

```jldoctest
julia> (A, B) = freeprecess(100, 1, 1000, 100, 3.75); A * Magnetization(1, 0, 0) + B
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048
```
