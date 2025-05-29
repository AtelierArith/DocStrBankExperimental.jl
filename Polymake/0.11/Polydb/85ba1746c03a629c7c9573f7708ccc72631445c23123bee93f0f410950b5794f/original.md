```
  getindex(db::Database, name::AbstractString)
```

Return a `Polymake.Polydb.Collection{Polymake.BigObject}` instance from `db` with the given `name`. Sections and collections in the name are connected with the '.' sign.

# Examples

```julia-repl
julia> db = Polymake.Polydb.get_db();

julia> collection = getindex(db, "Polytopes.Lattice.SmoothReflexive")
Polymake.Polydb.Collection{Polymake.BigObject}: Polytopes.Lattice.SmoothReflexive

julia> collection = db["Matroids.Small"]
Polymake.Polydb.Collection{Polymake.BigObject}: Matroids.Small
```
