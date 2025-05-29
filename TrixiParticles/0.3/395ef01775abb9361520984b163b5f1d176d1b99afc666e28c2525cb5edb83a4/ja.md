```
BoundaryZone(; plane, plane_normal, density, particle_spacing,
             initial_condition=nothing, extrude_geometry=nothing,
             open_boundary_layers::Integer, boundary_type=BidirectionalFlow())
```

[`OpenBoundarySPHSystem`](@ref)の境界ゾーン。

指定された平面（2Dの線または3Dの長方形）は、`plane_normal`の反対方向に押し出されて境界ゾーンのボックスが作成されます。境界ゾーンの実際の形状を指定する方法は3つあります。

1. `initial_condition`または`extrude_geometry`を渡さない。境界ゾーンのボックスは境界粒子で満たされます（デフォルト）。
2. 1D形状を2Dで、または2D形状を3Dで渡すことによって`extrude_geometry`を指定し、それが`plane_normal`の反対方向に押し出されて境界粒子が作成されます。

      * 2Dでは、形状は`plane`で指定された線上にある2D座標の初期条件である必要があります。または、y座標が`0`のときに`plane`で指定された線上にある1D座標の初期条件である必要があります。
      * 3Dでは、形状は`plane`で指定された長方形内にある3D座標の初期条件である必要があります。または、z座標が`0`のときに`plane`で指定された長方形内にある2D座標の初期条件である必要があります。
3. 2Dの初期条件を2Dで、または3Dの初期条件を3Dで渡すことによって`initial_condition`を指定し、これが境界粒子に使用されます。

!!! note
    境界ゾーンボックスの外にある粒子は削除されます。


# キーワード

  * `plane`: ドメインの表面の一部を定義する点のタプル。          点は2Dの線または3Dの長方形を形成する必要があります。          この線または長方形は、上流方向に押し出されて境界ゾーンが得られます。          2Dでは、2つの点$(A, B)$を渡し、区間$[A, B]$が          流入面となるようにします。          3Dでは、3つの点$(A, B, C)$を渡し、長方形の流入面が          ベクトル$\widehat{AB}$と$\widehat{AC}$によって形成されるようにします。          これら2つのベクトルは直交している必要があります。
  * `plane_normal`: 平面法線を定義するベクトル。常に流体ドメインの内部を指します。
  * `boundary_type=BidirectionalFlow()`: 境界のタイプを指定します。利用可能なタイプは

      * 流入境界のための`InFlow()`
      * 流出境界のための`OutFlow()`
      * 双方向流境界のための`BidirectionalFlow()`（デフォルト）
  * `open_boundary_layers`: `plane_normal`の反対方向の粒子層の数。
  * `particle_spacing`: 粒子間の間隔（[`InitialCondition`](@ref)を参照）。
  * `density`: 粒子密度（[`InitialCondition`](@ref)を参照）。
  * `initial_condition=nothing`: 流入粒子のための`InitialCondition`。                              境界ゾーンの外にある粒子は削除されます。                              `extrude_geometry`と一緒に使用しないでください。
  * `extrude_geometry=nothing`: 2Dでの1D形状または3Dでの2D形状で、平面上にあり、                             上流に押し出されて流入粒子を得るためのものです。                             詳細については上記のポイント2を参照してください。

# 例

```julia
# 2D
plane_points = ([0.0, 0.0], [0.0, 1.0])
plane_normal=[1.0, 0.0]

inflow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1, density=1.0,
                      open_boundary_layers=4, boundary_type=InFlow())

# 3D
plane_points = ([0.0, 0.0, 0.0], [1.0, 0.0, 0.0], [0.0, 1.0, 0.0])
plane_normal=[0.0, 0.0, 1.0]

outflow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1, density=1.0,
                       open_boundary_layers=4, boundary_type=OutFlow())

# 3D粒子を円柱としてサンプリング
circle = SphereShape(0.1, 0.5, (0.5, 0.5), 1.0, sphere_type=RoundSphere())

bidirectional_flow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1,
                                  density=1.0, extrude_geometry=circle, open_boundary_layers=4)
```

!!! warning "実験的実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

