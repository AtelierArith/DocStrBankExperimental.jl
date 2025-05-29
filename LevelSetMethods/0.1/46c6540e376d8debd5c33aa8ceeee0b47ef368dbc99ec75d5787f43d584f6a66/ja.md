```
LevelSetEquation(; terms, levelset, boundary_conditions, t = 0, integrator = RK3())
```

形 `ϕₜ + sum(terms) = 0` のレベルセット方程式を作成します。ここで、各 `t ∈ terms` は [`LevelSetTerm`](@ref) であり、`levelset` は初期の [`LevelSet`](@ref) です。

[`integrate!(ls, tf)`](@ref) を呼び出すと、レベルセット方程式が時間 `tf` まで進化し、その過程でオブジェクト `eq` の `current_state(eq)` と `current_time(eq)` が変更されます（したがって、元の `levelset` も変更されます）。

境界条件は2つの方法で指定できます。単一の `BoundaryCondition` が提供されると、それは領域のすべての境界に均一に適用されます。各境界に異なる境界条件を適用するには、領域の次元数と同じ数の要素を持つ `(bc_x, bc_y, ...)` の形のタプルを渡します。`bc_x` が `BoundaryCondition` の場合、それは `x` 方向の両方の境界に適用されます。`bc_x` が2つの `BoundaryCondition` のタプルである場合、最初のものが左の境界に適用され、2番目のものが右の境界に適用されます。他の次元にも同じ論理が適用されます。

オプションのパラメータ `t` はシミュレーションの初期時間を指定し、`integrator` はレベルセット方程式を進化させるために使用される [`TimeIntegrator`](@ref) です。

```jldoctest; output = true
using LevelSetMethods, StaticArrays
grid = CartesianGrid((-1, -1), (1, 1), (50, 50))    # グリッドを定義
ϕ = LevelSet(x -> x[1]^2 + x[2]^2 - 0.5^2, grid)    # 初期形状
𝐮 = MeshField(x -> SVector(1, 0), grid)             # 伝播速度
terms = (AdvectionTerm(𝐮),)            # 伝播と曲率の項
bc = PeriodicBC()                                   # 周期的境界条件
eq = LevelSetEquation(; terms, levelset = ϕ, bc)    # レベルセット方程式

# 出力

レベルセット方程式は次のように与えられます

 	 ϕₜ + 𝐮 ⋅ ∇ ϕ = 0

現在の時間 0.0

```
