```
MBProblem{T,DF,DP,RF,RP,L,R,M,IC,IE,FT}
```

`MBProblem`の定義。

# フィールド

  * `geometry::MBGeometry{T}`: 問題の幾何学。
  * `boundary_conditions::BoundaryConditions{L, R, M}`: 境界条件。
  * `diffusion_function::DF`: 拡散関数で、形式は`(u, x, t, p) -> Number`、ここで`p = diffusion_parameters`。
  * `diffusion_parameters::DP`: 拡散関数のパラメータ。
  * `reaction_function::RF`: 反応関数で、形式は`(u, x, t, p) -> Number`、ここで`p = reaction_parameters`。
  * `reaction_parameters::RP`: 反応関数のパラメータ。
  * `initial_condition::IC`: 初期条件で、`initial_condition[i]`は`geometry.mesh_points[i]`における値であり、`t = initial_time`に対応。
  * `initial_endpoint::IE`: 初期エンドポイント。これは`t = initial_time`における移動境界の値。
  * `initial_time::FT`: 初期時間。
  * `final_time::FT`: 最終時間。

[`SteadyMBProblem`](@ref)も参照してください。

# コンストラクタ

デフォルトコンストラクタを使用できますが、次のコンストラクタも提供しています。

```
MBProblem(;
    geometry, 
    boundary_conditions,
    diffusion_function,
    diffusion_parameters = nothing,
    reaction_function = Returns(0.0),
    reaction_parameters = nothing,
    initial_condition,
    initial_endpoint,
    initial_time = 0.0,
    final_time)
```

これにより、いくつかのデフォルト値が提供されます。さらに、`geometry`と`boundary_conditions`を提供する代わりに、次のように使用できます。

```
MBProblem(mesh_points, lhs, rhs, moving_boundary; kwargs...)
```

これにより、`geometry = MBGeometry(mesh_points)`および`boundary_conditions = BoundaryConditions(lhs, rhs, moving_boundary)`が構築されます。`kwargs...`は上記と同様ですが、もちろん`geometry`と`boundary_conditions`は含まれません。

`MBProblem`を解くには、DifferentialEquations.jlで行うように`solve`を使用します。例えば、

```
sol = solve(prob, TRBDF2(linsolve=KLUFactorization()), saveat=0.1)
```

は、`TRBDF2()`アルゴリズムを使用して問題を解き、関連する線形システムはスパースソルバー`KLUFactorization()`で解かれ、解は`initial_time`から`final_time`までの`0.1`単位の時間ごとに保存されます。この場合の解は、`sol.u[i]`が`sol.u[i][begin:(end-1)]`の`u`の値を持ち、移動境界の位置は`sol.t[i]`において`sol.u[i][end]`にあります。対応するグリッドポイントについては、[`scaled_mesh_points`](@ref)も参照してください。
