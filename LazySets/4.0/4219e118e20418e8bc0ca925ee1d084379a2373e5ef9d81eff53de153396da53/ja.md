```
plot3d(S::LazySet; [backend]=default_polyhedra_backend(S), [alpha]=1.0,
       [color]=:blue, [colormap]=:viridis, [colorrange]=nothing,
       [interpolate]=false, [overdraw]=false, [shading]=true,
       [transparency]=true, [visible]=true)
```

三次元セットを `Makie` を使用してプロットします。

### 入力

  * `S`            – セット
  * `backend`      – (オプション、デフォルト: `default_polyhedra_backend(S)`) 多面体計算のためのバックエンド
  * `alpha`        – (オプション、デフォルト: `1.0`) `[0,1]` の範囲の浮動小数点数; アルファまたは透明度の値
  * `color`        – (オプション、デフォルト: `:blue`) `Symbol` または `Colorant`; 主なプロット要素（マーカー、線など）の色で、`:red` のような色のシンボル/文字列で指定できます
  * `colormap`     – (オプション、デフォルト: `:viridis`) 主なプロットのカラーマップ; `available_gradients()` を使用して利用可能なグラデーションを確認できます。これらは `[:red, :black]` のように使用することもできます
  * `colorrange`   – (オプション、デフォルト: `nothing`, これは `Makie.Automatic()` にフォールバックします) `colormap` のインデックスに使用されるデータ範囲を指定するタプル `(min, max)`
  * `interpolate`  – (オプション、デフォルト: `false`) ヒートマップと画像のためのブール値; 近くのピクセル間の色の補間を切り替えます
  * `overdraw`     – (オプション、デフォルト: `false`)
  * `shading`      – (オプション、デフォルト: `true`) シェーディングを切り替えるブール値（メッシュ用）
  * `transparency` – (オプション、デフォルト: `true`) `true` の場合、セットは透明で、そうでない場合は固体オブジェクトとして表示されます
  * `visible`      – (オプション、デフォルト: `true`) プロットの可視性を切り替えるブール値

属性と使用法の完全なリストについては、[Makieのドキュメント](http://makie.juliaplots.org/stable/plot-attributes)を参照してください。

### 注意事項

このプロットレシピは、`S` の制約リストを計算し、H表現の多面体に変換することによって機能します。次に、この多面体は `Polyhedra.Mesh` で変換され、`mesh` 関数を使用してプロットされます。

関数 `constraints_list` があなたのセット `S` に適用できない場合は、まず過大近似を試してください。例えば、次のようにします。

```julia
julia> Sapprox = overapproximate(S, SphericalDirections(10))

julia> using Polyhedra, GLMakie

julia> plot3d(Sapprox)
```

上記の数 `10` は考慮される方向の数に対応します。より良い解像度を得るには、より高い値を使用してください（ただし、時間がかかります）。

効率を考慮して、次のように `CDDLib` バックエンドを使用することを検討してください。

```julia
julia> using CDDLib

julia> plot3d(Sapprox, backend=CDDLib.Library())
```

### 例

この機能は、`Polyhedra` と `Makie` バックエンドの両方を必要とします。`LazySets` をロードした後、`using Polyhedra, GLMakie`（または別のMakieバックエンド）を実行します。

```julia
julia> using LazySets, Polyhedra, GLMakie

julia> plot3d(10 * rand(Hyperrectangle, dim=3))

julia> plot3d!(10 * rand(Hyperrectangle, dim=3), color=:red)
```
