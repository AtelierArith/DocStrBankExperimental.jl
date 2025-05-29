```
  getindex(db::Database, name::AbstractString)
```

与えられた `name` を持つ `db` から `Polymake.Polydb.Collection{Polymake.BigObject}` インスタンスを返します。名前のセクションとコレクションは '.' 記号で接続されています。

# 例

```julia-repl
julia> db = Polymake.Polydb.get_db();

julia> collection = getindex(db, "Polytopes.Lattice.SmoothReflexive")
Polymake.Polydb.Collection{Polymake.BigObject}: Polytopes.Lattice.SmoothReflexive

julia> collection = db["Matroids.Small"]
Polymake.Polydb.Collection{Polymake.BigObject}: Matroids.Small
```
