```
InfiniteWall{N, OT <: ObstacleType}(support::SVector{N, Float64}, normal::SVector{N, Float64})
```

任意の法線ベクトルを持つ無限壁障害物タイプ。法線ベクトルは壁の外側を指し、単位長さに正規化されている必要があります。型パラメータ `N` はシステムの次元を指し、`OT` は障害物のタイプで、`Absorbing` または `Reflecting` のいずれかです。

コンストラクタ:

```
InfiniteWall(support::AbstractVector, φ::Float64)
```

ここで、φは壁の法線の方向をラジアンで示します。

```
makewall(T::Type{<:InfiniteWall{2}}, p1::SVector{2, Float64}, p2::SVector{2, Float64})=
makewall(T::Type{<:InfiniteWall{3}}, p1::SVector{3, Float64}, p2::SVector{3, Float64}, p3::SVector{3, Float64}) =
```

2点または3点から壁を構築するためのものです。

`Absorbing` 壁に対しては粒子相互作用のデフォルト実装が提供されています。反射壁との相互作用は、次のように定義することで追加できます:

```julia
    function InPartS.obstacleforces!(so::InfiniteWall{DIMENSION, Reflecting}, p::YourParticleType, sim::Simulation)
        # ...
    end
```
