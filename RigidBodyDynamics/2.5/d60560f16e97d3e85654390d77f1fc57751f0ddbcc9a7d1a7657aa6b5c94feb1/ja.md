```julia
struct StateCache{M, JointCollection} <: RigidBodyDynamics.AbstractTypeDict
```

さまざまなスカラー型の[`MechanismState`](@ref)オブジェクトの作成と保存を管理するコンテナで、特定の`Mechanism`に関連付けられています。

`StateCache`は、`MechanismState`オブジェクトを使用する汎用関数を書くために使用でき、関数が呼び出されるたびに特定のスカラー型の新しい`MechanismState`を構築することによるオーバーヘッドを回避します。

# 例

```julia-repl
julia> mechanism = rand_tree_mechanism(Float64, Revolute{Float64}, Prismatic{Float64}, QuaternionFloating{Float64});

julia> cache = StateCache(mechanism)
StateCache{…}

julia> state32 = cache[Float32]
MechanismState{Float32, Float64, Float64, …}(…)

julia> cache[Float32] === state32
true

julia> cache[Float64]
MechanismState{Float64, Float64, Float64, …}(…)
```
