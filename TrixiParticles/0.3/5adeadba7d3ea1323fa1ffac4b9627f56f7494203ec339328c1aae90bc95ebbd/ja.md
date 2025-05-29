```
extrude_geometry(geometry; particle_spacing, direction, n_extrude::Integer,
                 velocity=zeros(length(direction)),
                 mass=nothing, density=nothing, pressure=0.0)
```

特定の方向に沿って線、平面、または形状を押し出します。 [`InitialCondition`](@ref) を返します。

# 引数

  * `geometry`:           粒子座標または 2D 形状を 3D ボリュームに押し出すための [`InitialCondition`](@ref) であるか、2D の点 $(A, B)$ のペアで、2D の平面に押し出すための区間 $[A, B]$ を定義します。または、3D の点 $(A, B, C)$ のペアで、ベクトル $\widehat{AB}$ と $\widehat {AC}$ によって広がる平行四辺形を定義し、平行六面体に押し出します。

# キーワード

  * `particle_spacing`:   粒子間の間隔。 `geometry` が `InitialCondition` の場合は省略できます（ただし、`geometry.particle_spacing == -1` の場合を除く）。
  * `direction`:          押し出す方向を指定するベクトル。
  * `n_extrude`:          押し出し方向に作成される粒子の層の数。
  * `velocity`:           各粒子の座標をその速度にマッピングする関数、または定常流体速度の場合はこの速度を保持するベクトル。デフォルトでは速度はゼロです。
  * `mass`:               粒子の密度と間隔から自動的に粒子の質量を計算するための `nothing`（デフォルト）、または各粒子の座標をその質量にマッピングする関数、またはすべての粒子に対して一定の質量のスカラー。
  * `density`:            各粒子の座標をその密度にマッピングする関数、またはすべての粒子に対して一定の密度のスカラー。
  * `pressure`:           すべての粒子の圧力をこの値に設定するためのスカラー。これは [`EntropicallyDampedSPHSystem`](@ref) にのみ使用され、システム内で初期圧力関数を使用する際に上書きされます。
  * `tlsph`:              [`TotalLagrangianSPHSystem`](@ref) では、粒子は流体のように粒子半径の距離ではなく、形状の境界に配置する必要があります。 `tlsph=true` の場合、粒子は形状の境界に配置されます。

# 例

```jldoctest; output = false
# 2D の線を 2D の平面に押し出す
p1 = [0.0, 0.0]
p2 = [1.0, 1.0]

direction = [-1.0, 1.0]

shape = extrude_geometry((p1, p2); direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# 3D の平行四辺形を 3D の平行六面体に押し出す
p1 = [0.0, 0.0, 0.0]
p2 = [0.5, 1.0, 0.0]
p3 = [1.0, 0.2, 0.0]

direction = [0.0, 0.0, 1.0]

shape = extrude_geometry((p1, p2, p3); direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# 2D 形状（ここでは円）を 3D 形状（ここでは円柱）に押し出す
shape = SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, n_layers=3,
                    sphere_type=RoundSphere(end_angle=pi))

direction = [0.0, 0.0, 1.0]

shape = extrude_geometry(shape; direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# 出力
┌ Info: 望ましいサイズは粒子間隔 0.1 の倍数ではありません。
└ 新しい粒子間隔は 0.09387239731236392 に設定されました。
┌ Info: 望ましいサイズは粒子間隔 0.1 の倍数ではありません。
└ 新しい粒子間隔は 0.09198039027185569 に設定されました。
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 3                                                                │
│ #particles: ………………………………………………… 144                                                              │
│ particle spacing: ………………………………… 0.1                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

!!! warning "実験的実装"
    これは実験的な機能であり、今後のリリースで変更される可能性があります。

