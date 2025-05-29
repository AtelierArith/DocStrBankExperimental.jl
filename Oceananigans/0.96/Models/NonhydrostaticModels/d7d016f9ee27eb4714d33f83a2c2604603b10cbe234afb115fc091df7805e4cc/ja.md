```
set!(model::NonhydrostaticModel; enforce_incompressibility=true, kwargs...)
```

`model`の速度およびトレーサーフィールドを設定します。キーワード引数`kwargs...`は`name=data`の形式を取り、`name`は`model.velocities`または`model.tracers`のフィールドの1つを指し、`data`は配列、引数`(x, y, z)`を持つ関数、または`set!(ϕ::AbstractField, data)`関数が存在する任意のデータ型である可能性があります。

# 例

```julia
model = NonhydrostaticModel(grid=RectilinearGrid(size=(32, 32, 32), length=(1, 1, 1))

# uをzの放物線関数に、vを上部と下部で減衰したランダム数に設定し、
# Tを半分ゼロ、半分ランダム数のいくつかのばかげた配列に設定します。

u₀(x, y, z) = z / model.grid.Lz * (1 + z / model.grid.Lz)
v₀(x, y, z) = 1e-3 * rand() * u₀(x, y, z)

T₀ = rand(size(model.grid)...)
T₀[T₀ .< 0.5] .= 0

set!(model, u=u₀, v=v₀, T=T₀)
```
