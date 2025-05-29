```
single_particle_density(dvec; component)
single_particle_density(add; component)
```

ベクトル `dvec` またはアドレス `add` の対角単一粒子密度を計算します。`component` 引数が指定されている場合は、アドレスのその成分のみが考慮されます。結果は常に正規化されており、`sum(result) ≈ num_particles(address)` となります。

# 例

```jldoctest
julia> v = DVec(fs"|⋅↑⇅↓⋅⟩" => 1.0, fs"|↓↓⋅↑↑⟩" => 0.5)
DVec{FermiFS2C{2, 2, 5, 4, FermiFS{2, 5, BitString{5, 1, UInt8}}, FermiFS{2, 5, BitString{5, 1, UInt8}}},Float64} with 2 entries, style = IsDeterministic{Float64}()
  fs"|↓↓⋅↑↑⟩" => 0.5
  fs"|⋅↑⇅↓⋅⟩" => 1.0

julia> single_particle_density(v)
(0.2, 1.0, 1.6, 1.0, 0.2)

julia> single_particle_density(v; component=1)
(0.0, 0.8, 0.8, 0.2, 0.2)
```

# 参照

  * [`SingleParticleDensity`](@ref)
