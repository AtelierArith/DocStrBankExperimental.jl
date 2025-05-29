```
FermiFS2C <: AbstractFockAddress
FermiFS2C(onr_a, onr_b)
```

2つのフェルミオン（スピン）成分を持つフォック状態アドレス。2つの[`FermiFS`](@ref)成分を持つ[`CompositeFS`](@ref)のエイリアス。互換性のある2つの[`FermiFS`](@ref)、2つの[`onr`](@ref)、またはモードの数に続いて`mode => occupation_number`のペアを指定することで構築します。ここで、`occupation_number=1`は最初の成分に粒子を置き、`occupation_number=-1`は2番目の成分に粒子を置きます。以下に例を示します。

# 例

```jldoctest
julia> FermiFS2C(FermiFS(1,0,0), FermiFS(0,1,1))
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> FermiFS2C((1,0,0), (0,1,1))
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> FermiFS2C(3, 1 => 1, 2 => -1, 3 => -1)
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> fs"|↑↓↓⟩"
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)
```
