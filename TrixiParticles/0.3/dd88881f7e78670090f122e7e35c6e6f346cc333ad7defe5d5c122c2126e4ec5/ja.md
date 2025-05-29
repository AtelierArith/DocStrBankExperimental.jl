```
SignedDistanceField(geometry, particle_spacing;
                    points=nothing,
                    max_signed_distance=4 * particle_spacing,
                    use_for_boundary_packing=false)
```

複雑なジオメトリの表面に沿って粒子を生成し、この表面への符号付き距離と法線を保存します。

# 引数

  * `geometry`: [`load_geometry`](@ref) によって返されるジオメトリ。
  * `particle_spacing`: 粒子間の間隔。

# キーワード

  * `max_signed_distance`:      保存される最大符号付き距離。つまり、形状の表面からの距離が                             `abs(max_signed_distance)` の粒子のみがサンプリングされます。
  * `points`:                   符号付き距離が計算される点。                             `nothing`（デフォルト）の場合、形状のバウンディングボックスが                             一様なグリッドの点でサンプリングされます。
  * `use_for_boundary_packing`: [`SignedDistanceField`] が境界 [`ParticlePackingSystem`](@ref) をパックするために使用される場合は                             `true` に設定します。境界なしでパックする場合は                             デフォルトの `false` を使用します。
