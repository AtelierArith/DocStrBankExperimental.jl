```
excite(spin, rf::InstantaneousRF, [nothing])
excite(spin, rf::RF, [workspace])
```

与えられたスピンの励起をシミュレートします。`(A, B)`を返し、`A * M + B`が磁化`M`に励起を適用します。`B`が`isnothing`である場合（`InstantaneousRF`の場合）、`A * M`が`M`に励起を適用します。

`RF`オブジェクトの場合、`workspace isa ExcitationWorkspace`です。`SpinMC`オブジェクトの場合、Bloch-McConnell方程式を解くために近似行列指数を使用するには、`workspace = ExcitationWorkspace(spin, nothing)`を使用します。

インプレースバージョンについては、[`excite!`](@ref)を参照してください。

# 例

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75); s.M
磁化ベクトルの型はFloat64:
 Mx = 0.0
 My = 0.0
 Mz = 1.0

julia> (A,) = excite(s, InstantaneousRF(π/2, π/4)); A * s.M
磁化ベクトルの型はFloat64:
 Mx = 0.7071067811865476
 My = -0.7071067811865475
 Mz = 6.123233995736766e-17
```
