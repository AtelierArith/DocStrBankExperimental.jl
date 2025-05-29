```
ScalarBiharmonicDiffusivity(formulation = ThreeDimensionalFormulation(), FT = Float64;
                            ν = 0,
                            κ = 0,
                            discrete_form = false,
                            loc = (nothing, nothing, nothing),
                            parameters = nothing)
```

粘度係数 `ν` と `tracers` の各トレーサーフィールドに対するトレーサー拡散率 `κ` を持つスカラー双調和拡散閉じ込めを返します。単一の `κ` が提供される場合、それはすべてのトレーサーに適用されます。そうでない場合、`κ` は各トレーサーの値を持つ `NamedTuple` でなければなりません。

# 引数

  * `formulation`:

      * 水平方向に適用される拡散率のための `HorizontalFormulation()`
      * 垂直方向に適用される拡散率のための `VerticalFormulation()`
      * すべての方向に等方的に適用される拡散率のための `ThreeDimensionalFormulation()` (デフォルト)
  * `FT`: 浮動小数点データ型 (デフォルト: `Float64`)

# キーワード引数

  * `ν`: 粘度。`Number`、`AbstractArray`、`Field`、または `Function`。
  * `κ`: 拡散率。`Number`、`AbstractArray`、`Field`、`Function`、または各トレーサーのエントリを持つ拡散率の `NamedTuple`。
  * `discrete_form`: `Boolean`；デフォルト: `false`。
  * `required_halo_size = 2`: 閉じ込めに必要なハローサイズ。この値は整数である必要があります。`ν` または `κ` のためにハローサイズが1より大きい関数を使用する場合のみ変更してください。

粘度または拡散率を関数として指定する場合、キーワード引数 `discrete_form` の値に応じて、コンストラクタは次のことを期待します：

  * `discrete_form = false` (デフォルト)：グリッドのネイティブ座標と時間の関数、例えば、`RectilinearGrid` のための `(x, y, z, t)` または `LatitudeLongitudeGrid` のための `(λ, φ, z, t)`。
  * `discrete_form = true`:

      * `loc = (nothing, nothing, nothing)` (デフォルト)：`(i, j, k, grid, ℓx, ℓy, ℓz)` の関数で、`ℓx`、`ℓy`、`ℓz` は `Face()` または `Center()` のいずれか。
      * `loc = (ℓx, ℓy, ℓz)` で `ℓx`、`ℓy`、`ℓz` が `Face()` または `Center()` のいずれか：`(i, j, k, grid)` の関数。
  * `parameters`: 粘度および/または拡散率を計算する関数で使用されるパラメータの `NamedTuple`；デフォルト: `nothing`。

例については [`ScalarDiffusivity`](@ref) を参照してください。
