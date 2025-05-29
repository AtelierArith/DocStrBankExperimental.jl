```
freeprecess(spin, t, [nothing])
freeprecess(spinmc, t, [workspace])
freeprecess(spin, t, grad, [nothing])
freeprecess(spinmc, t, grad, [workspace])
```

与えられたスピンに対して、時間 `t` ms の自由前処理をシミュレートします。オプションで B0 勾配の存在下で行うことができます。`A * M + B` が磁化 `M` に自由前処理を適用するように、`(A, B)` を返します。

`SpinMC` オブジェクトの場合、`workspace isa BlochMcConnellWorkspace` です。代わりに `nothing` を渡すと、Bloch-McConnell 方程式を解くために近似行列指数を使用します。

インプレースバージョンについては、[`freeprecess!`](@ref) を参照してください。

# 例

```jldoctest
julia> s = Spin(Magnetization(1, 0, 0), 1, 1000, 100, 3.75)
Spin{Float64}:
 M = Magnetization(1.0, 0.0, 0.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 3.75 Hz
 pos = Position(0.0, 0.0, 0.0) cm

julia> (A, B) = freeprecess(s, 100); A * s.M + B
磁化ベクトルの型は Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048

julia> s = Spin(Magnetization(1, 0, 0), 1, 1000, 100, 0, Position(0, 0, 3.75))
Spin{Float64}:
 M = Magnetization(1.0, 0.0, 0.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(0.0, 0.0, 3.75) cm

julia> (A, B) = freeprecess(s, 100, Gradient(0, 0, 1/GAMBAR)); A * s.M + B
磁化ベクトルの型は Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048
```
