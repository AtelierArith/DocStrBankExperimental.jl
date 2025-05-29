```
viz(opf::MultiScaleTreeGraph.Node; kwargs...)
viz!(opf::MultiScaleTreeGraph.Node; kwargs...)
```

MTGの3Dジオメトリを視覚化します（通常はOPFから読み取ります）。この関数は、MTGの各ノードで`:geometry`属性を検索し、`mesh`フィールドを使用して視覚化を構築します。もしそれが欠けている場合は、参照メッシュと関連する変換行列を使用します。

`:geometry`属性は通常、最初に`refmesh_to_mesh!`関数によって追加され、これは`transform!`関数で呼び出すことができます。以下の例を参照してください。

# 引数

  * `opf`: 視覚化されるMTG。
  * `kwargs`: `viz!`に渡される追加の引数で、以下が含まれます：

      * `color`: プロットに使用される色。色素、MTGの属性（シンボルとして指定）、または各参照メッシュの色の辞書である可能性があります。
      * `colormap`: プロットに使用されるカラースキーム。シンボルまたはColorSchemeである可能性があります。
      * `segmentcolor`: ファセットに使用される色。色素または色のシンボルである必要があります。
      * `showsegments`: ファセットを表示するかどうかを示すブール値。
      * `color_missing`: 欠損値に使用される色。色素または色のシンボルである必要があります。
      * `color_vertex`: `color`（属性によって色付けされている場合）の値がメッシュの各頂点に対して定義されているか、各メッシュに対して定義されているかを示すブール値。
      * `index`: 視覚化される属性値のインデックスを指定する整数。この属性が*e.g.* 各タイムステップの値のベクトルである場合に便利です。
      * `color_cache_name`: 色キャッシュの名前。文字列である必要があります（デフォルトはランダムな文字列）。
      * `filter_fun`: プロットされるノードをフィルタリングする関数。ノードを引数として受け取り、ブール値を返す関数である必要があります。
      * `symbol`: このシンボルを持つノードのみをプロットします。文字列またはベクトルである必要があります。
      * `scale`: このスケールを持つノードのみをプロットします。整数またはベクトルである必要があります。
      * `link`: このリンクを持つノードのみをプロットします。文字列またはベクトルである必要があります。

`color_vertex`はデフォルトで`false`に設定されています。

# 例

```julia
using MultiScaleTreeGraph, PlantGeom, GLMakie

file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
# file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","coffee.opf")

opf = read_opf(file)
viz(opf)

# opfを何度もプロットする必要がある場合は、ノードジオメトリにメッシュをキャッシュする方が良いです
# このように：
transform!(opf, refmesh_to_mesh!)

# その後、以前のように再度プロットすると、より速くなります：
viz(opf)

# 3Dプロットにさまざまなオプションで色を付けることもできます：
# 1つの共有色で：
viz(opf, color = :red)
# 参照メッシュごとに1色：
viz(opf, color = Dict(1 => :burlywood4, 2 => :springgreen4, 3 => :burlywood4))

# または一部の色を変更するだけ：
viz(opf, color = Dict(1 => :burlywood4))

# またはopf属性によって色付けする、例えばメッシュの最大Z座標を使用する（注意：使用する必要があります
# `refmesh_to_mesh!`の前に、上記を参照）：
transform!(opf, zmax => :z_max, ignore_nothing = true)
viz(opf, color = :z_max)

# 参照メッシュ1の各頂点に対して1色：
using Meshes
vertex_color = get_color(1:nvertices(get_ref_meshes(opf))[1], [1,nvertices(get_ref_meshes(opf))[1]])
viz(opf, color = Dict(1 => vertex_color))

# または各頂点のZ座標の値によって色付けすることもできます：
transform!(opf, :geometry => (x -> [Meshes.coords(i).z for i in Meshes.vertices(x.mesh)]) => :z, ignore_nothing = true)
viz(opf, color = :z, showsegments = true)

f,a,p = viz(opf, color = :z, showsegments = true)
p[:color] = :Length
```

```
viz!(ref_meshes; kwargs...)
```

Makieを使用して、すべての参照メッシュを単一の3Dプロットにプロットします。

# 例

```julia
using PlantGeom, GLMakie

file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)
meshes = get_ref_meshes(opf)

viz(meshes)
# 1つの共有色で：
viz(meshes, color = :green)
# 参照メッシュごとに1色：
viz(meshes, color = Dict(1 => :burlywood4, 2 => :springgreen4, 3 => :burlywood4))
# または一部の色を変更するだけ：
viz(meshes, color = Dict(1 => :burlywood4, 3 => :burlywood4))
# 参照メッシュ0の各頂点に対して1色：
viz(meshes, color = Dict(2 => 1:nvertices(meshes)[2]))
```
