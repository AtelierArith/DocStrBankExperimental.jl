```
スカラー拡散率(time_discretization = 明示的時間離散化(),
                  formulation = 三次元定式化(), FT = Float64;
                  ν = 0,
                  κ = 0,
                  discrete_form = false,
                  loc = (nothing, nothing, nothing),
                  parameters = nothing)
```

`スカラー拡散率` turbulence closure を粘度 `ν` と `tracers` の各トレーサーフィールドに対するトレーサー拡散率 `κ` で返します。単一の `κ` が提供されると、それはすべてのトレーサーに適用されます。そうでない場合、`κ` は各トレーサーの値を持つ `NamedTuple` でなければなりません。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()`（デフォルト）または `VerticallyImplicitTimeDiscretization()` のいずれか。
  * `formulation`:

      * 水平方向に適用される拡散率のための `HorizontalFormulation()`
      * 垂直方向に適用される拡散率のための `VerticalFormulation()`
      * すべての方向に等方的に適用される拡散率のための `ThreeDimensionalFormulation()`（デフォルト）
  * `FT`: 浮動小数点データ型（デフォルト: `Float64`）

# キーワード引数

  * `ν`: 粘度。`Number`、`AbstractArray`、`Field`、または `Function`。
  * `κ`: 拡散率。`Number`、`AbstractArray`、`Field`、`Function`、または各トレーサーのエントリを持つ拡散率の `NamedTuple`。
  * `discrete_form`: `Boolean`；デフォルト: `false`。

粘度または拡散率を関数として指定する場合、キーワード引数 `discrete_form` の値に応じて、コンストラクタは次のことを期待します：

  * `discrete_form = false`（デフォルト）：グリッドのネイティブ座標と時間の関数、例えば、`(x, y, z, t)` は `RectilinearGrid` のため、または `(λ, φ, z, t)` は `LatitudeLongitudeGrid` のため。
  * `discrete_form = true`:

      * `loc = (nothing, nothing, nothing)` かつ `parameters = nothing`（デフォルト）：`(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields)` の関数で、`ℓx`、`ℓy`、`ℓz` は `Face()` または `Center()` のいずれか。
      * `loc = (ℓx, ℓy, ℓz)` で `ℓx`、`ℓy`、`ℓz` が `Face()` または `Center()` であり、`parameters = nothing`：`(i, j, k, grid, clock, fields)` の関数。
      * `loc = (nothing, nothing, nothing)` かつ指定された `parameters`：`(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields, parameters)` の関数。
      * `loc = (ℓx, ℓy, ℓz)` かつ指定された `parameters`：`(i, j, k, grid, clock, fields, parameters)` の関数。
  * `required_halo_size = 1`: クローズのために必要なハローサイズ。この値は整数である必要があります。`ν` または `κ` のためにハローサイズが1より大きい関数を使用する場合のみ変更してください。
  * `parameters`: 粘度および/または拡散率を計算する関数で使用される `NamedTuple`；デフォルト: `nothing`。

# 例

```jldoctest スカラー拡散率
julia> using Oceananigans

julia> スカラー拡散率(ν=1000, κ=2000)
スカラー拡散率{明示的時間離散化}(ν=1000.0, κ=2000.0)
```

```jldoctest スカラー拡散率
julia> const depth_scale = 100;

julia> @inline ν(x, y, z, t) = 1000 * exp(z / depth_scale)
ν (generic function with 1 method)

julia> スカラー拡散率(ν=ν)
スカラー拡散率{明示的時間離散化}(ν=ν (generic function with 1 method), κ=0.0)
```

```jldoctest スカラー拡散率
julia> using Oceananigans.Grids: znode

julia> @inline function κ(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields)
           z = znode(i, j, k, grid, ℓx, ℓy, ℓz)
           return 2000 * exp(z / depth_scale)
       end
κ (generic function with 1 method)

julia> スカラー拡散率(κ=κ, discrete_form=true)
スカラー拡散率{明示的時間離散化}(ν=0.0, κ=Oceananigans.TurbulenceClosures.DiscreteDiffusionFunction{Nothing, Nothing, Nothing, Nothing, typeof(κ)})
```

```jldoctest スカラー拡散率
julia> @inline function another_κ(i, j, k, grid, clock, fields, p)
           z = znode(i, j, k, grid, Center(), Center(), Face())
           return 2000 * exp(z / p.depth_scale)
       end
another_κ (generic function with 1 method)

julia> スカラー拡散率(κ=another_κ, discrete_form=true, loc=(Center, Center, Face), parameters=(; depth_scale = 120.0))
スカラー拡散率{明示的時間離散化}(ν=0.0, κ=Oceananigans.TurbulenceClosures.DiscreteDiffusionFunction{Center, Center, Face, @NamedTuple{depth_scale::Float64}, typeof(another_κ)})
```
