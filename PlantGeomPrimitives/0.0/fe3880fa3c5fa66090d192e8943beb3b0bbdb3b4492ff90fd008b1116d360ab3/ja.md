```
properties(mesh::Mesh)
```

メッシュのプロパティを取得します。プロパティは、プロパティのタイプごとに1つのエントリを持つ辞書として保存されます。各プロパティは、三角形ごとに1つのオブジェクトの配列です。各プロパティはシンボルによって識別されます（例：）。

# 引数

  * `mesh`: 法線を取得するメッシュ。

# 戻り値

メッシュの法線を含むベクター。

# 例

```jldoctest; output=false
julia> r = Rectangle();

julia> add_property!(r, :absorbed_PAR, [0.0, 0.0]);

julia> properties(r);
```
