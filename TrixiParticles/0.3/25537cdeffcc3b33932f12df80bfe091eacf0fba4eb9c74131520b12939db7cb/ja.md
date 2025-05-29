```
ParticlePackingSystem(shape::InitialCondition;
                      signed_distance_field::SignedDistanceField,
                      smoothing_kernel=SchoenbergQuinticSplineKernel{ndims(shape)}(),
                      smoothing_length=shape.particle_spacing,
                      smoothing_length_interpolation=smoothing_length,
                      is_boundary=false, boundary_compress_factor=1,
                      neighborhood_search=GridNeighborhoodSearch{ndims(shape)}(),
                      background_pressure, tlsph=true, fixed_system=false)
```

複雑な形状のためのボディフィット粒子を生成するシステム。メソッドの詳細については、以下の説明を参照してください。

# 引数

  * `shape`: [`InitialCondition`](@ref) をパックするためのもの。

# キーワード

  * `background_pressure`:   粒子を物理的にパックするための定常背景圧力。                          大きな `background_pressure` は高い加速度を引き起こす可能性があり、                          適切に調整されたタイムステップが必要です。
  * `tlsph`:                 [`TotalLagrangianSPHSystem`](@ref) とともに、粒子は                          形状の境界に配置する必要があり、流体のように半分の粒子間隔ではありません。                          `tlsph=true` の場合、粒子は形状の境界に配置されます。
  * `is_boundary`:           `shape` が `signed_distance_field` を作成するために使用されたジオメトリの内部にある場合、                          `is*boundary=false` を設定します。                          そうでない場合（`shape` がサンプリングされた境界である場合）、                          `is*boundary=true` を設定します。                          境界の厚さは、次のようにして `signed*distance*field` を作成することで指定されます：                             -`use*for*boundary*packing=true`-`max*signed*distance=boundary*thickness`[`SignedDistanceField`](@ref) を参照してください。
  * `fixed_system`:          `true` に設定すると、システムは静的に保たれ、粒子は                          移動せず、`InitialCondition` は変更されません。                          これは、別の（非固定）`ParticlePackingSystem` と一緒にシステムがパックされる場合に便利です。                          この場合、固定システムと非固定システムの両方に対して                          `SignedDistanceField` は必要ありません（サイン距離フィールドとして `nothing` を使用します）。
  * `signed_distance_field`: 粒子を表面に制約するためには、                          粒子から面までの符号付き距離に関する情報が必要です。                          事前に計算された符号付き距離は、パッキング手順中に                          各粒子に補間されます。
  * `smoothing_kernel`:      このシステムで使用されるスムージングカーネル。                          [スムージングカーネル](@ref smoothing_kernel) を参照してください。
  * `smoothing_length`:      勾配推定に使用されるスムージング長。                          [スムージングカーネル](@ref smoothing_kernel) を参照してください。
  * `smoothing_length_interpolation`: `SignedDistanceField` 情報を補間するために使用されるスムージング長。                                   デフォルトは `smoothing_length_interpolation = smoothing_length` です。
