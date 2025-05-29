```
sample_boundary(signed_distance_field::SignedDistanceField;
                boundary_thickness::Real, tlsph=true)
```

複雑なジオメトリの[`SignedDistanceField`](@ref)を使用して境界粒子をサンプリングします。

# 引数

  * `signed_distance_field`: ジオメトリの符号付き距離場（[`SignedDistanceField`](@ref）を参照）。

# キーワード

  * `boundary_thickness`: 境界の厚さ
  * `tlsph`             : `tlsph=true`の場合、境界粒子はジオメトリの表面から1粒子の間隔で配置されます。そうでない場合、`tlsph=true`（流体粒子をシミュレート）では、境界粒子は表面から半粒子の間隔で配置されます。

# 例

```jldoctest; output = false, setup = :(particle_spacing = 0.03; boundary_thickness = 4 * particle_spacing; file = joinpath(pkgdir(TrixiParticles, "examples", "preprocessing", "data"), "circle.asc"))
geometry = load_geometry(file)

signed_distance_field = SignedDistanceField(geometry, particle_spacing;
                                            use_for_boundary_packing=true,
                                            max_signed_distance=boundary_thickness)

boundary_sampled = sample_boundary(signed_distance_field; boundary_density=1.0,
                                   boundary_thickness)

# output
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 2                                                                │
│ #particles: ………………………………………………… 889                                                              │
│ particle spacing: ………………………………… 0.03                                                             │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
