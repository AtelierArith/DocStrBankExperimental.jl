```
ComplexShape(geometry::Union{TriangleMesh, Polygon}; particle_spacing, density,
             pressure=0.0, mass=nothing, velocity=zeros(ndims(geometry)),
             point_in_geometry_algorithm=WindingNumberJacobson(; geometry,
                                                               hierarchical_winding=false,
                                                               winding_number_factor=sqrt(eps())),
             grid_offset::Real=0.0, max_nparticles=10^7,
             pad_initial_particle_grid=2particle_spacing)
```

粒子を用いて複雑なジオメトリをサンプリングします。[`InitialCondition`](@ref)を返します。ジオメトリのバウンディングボックス内に初期粒子グリッドが生成されることに注意してください。`point_in_geometry_algorithm`は、粒子がジオメトリ内にあるかどうかをチェックします。メソッドの詳細については、[`WindingNumberJacobson`](@ref)または[`WindingNumberHormann`](@ref)を参照してください。

# 引数

  * `geometry`: [`load_geometry`](@ref)によって返されるジオメトリ。

# キーワード

  * `particle_spacing`:   粒子間の間隔。
  * `density`:            各粒子の座標をその密度にマッピングする関数、                       またはすべての粒子に対して一定の密度のスカラー。
  * `velocity`:           各粒子の座標をその速度にマッピングする関数、                       または一定の流体速度の場合、この速度を保持するベクトル。                       デフォルトでは速度はゼロです。
  * `mass`:               粒子密度と間隔から粒子質量を自動的に計算するための`nothing`（デフォルト）、                       または各粒子の座標をその質量にマッピングする関数、                       またはすべての粒子に対して一定の質量のスカラー。
  * `pressure`:           すべての粒子の圧力をこの値に設定するためのスカラー。                       これは[`EntropicallyDampedSPHSystem`](@ref)によってのみ使用され、                       システム内で初期圧力関数を使用する際に上書きされます。
  * `point_in_geometry_algorithm`: 粒子を用いて複雑なジオメトリをサンプリングするためのアルゴリズム。                                基本的に、粒子がオブジェクト内にあるかどうかをチェックします。                                詳細については、[`WindingNumberJacobson`](@ref)または[`WindingNumberHormann`](@ref)を参照してください。
  * `grid_offset`: `geometry`のバウンディングボックスの初期粒子グリッドのオフセット。
  * `max_nparticles`: 初期粒子グリッド内の最大粒子数。                   これは、ジオメトリのスケールに対して小さすぎる`particle_spacing`                   を誤って選択するのを避けるためにのみ使用されます。
  * `pad_initial_particle_grid`: 初期粒子グリッドのパディング。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

