```
save_mesh(mesh; fileformat = :STL_BINARY, filename)
```

メッシュをさまざまな形式で外部ファイルに保存します。

# 引数

  * `mesh`: `Mesh`型のオブジェクト。
  * `fileformat`: メッシュを保存する形式を示すシンボル。
  * `filename`: メッシュを保存するファイルの名前を示す文字列。

# 詳細

`fileformat`は次のいずれかの引数を取る必要があります: `:STL_BINARY`, `:STL_ASCII`, `:PLY_BINARY`, `:PLY_ASCII`または`:OBJ`。これらの名前はシンボルとして渡す必要があります。

# 例

```julia
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> mesh = Mesh(v);

julia> save_mesh(mesh, fileformat = :STL_BINARY, filename = "path/to/mesh.bstl");
```
