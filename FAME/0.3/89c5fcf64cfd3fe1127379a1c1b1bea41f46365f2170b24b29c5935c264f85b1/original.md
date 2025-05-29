```
writefame(db, data; options)
```

Write Julia data to a FAME database.

### Arguments:

  * `db` can be a string containing the path to a FAME .db file or an instance of [`FameDatabase`](@ref).
  * `data` is a collection of data which will be written to the database.

      * If `data` is an `MVTSeries`, each series will be written to the database.
      * If `data` is a `Workspace`, each element will be written as a separate FAME object. In this case any nested `Workspace` of `MVTSeries` objects will be written recursively by prepending the names.

### Options:

  * `mode::Symbol` - if `db` is a string, the database is opened with the given `mode`. The default is :overwrite.
  * `prefix::Union{Nothing,String}` - the given `prefix` will be prepended to the name of each object written in the database. The default is `nothing`, i.e. nothing will be prepended. NOTE: `prefix=nothing` and `prefix=""` are not the same.
  * `glue::String` - the `glue` is used to join the prefix to the name. The default is `"_"`.

### Examples:

```
julia> w = Workspace(; a=1, b=TSeries(2020Q1,ones(10)), s=MVTSeries(2020M1, collect("ab"), randn(24,2)))
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  s ⇒ 24×2 MVTSeries{Monthly} with range 2020M1:2021M12 and variables …

julia> writefame("w.db", w)

julia> listdb("w.db")
2-element Vector{FAME.FameObject}:
 A: scalar,precision,undefined,0:0,0:0
 B: series,precision,quarterly_december,2020:1,2022:2
 S_A: series,precision,monthly,2020:1,2021:12
 S_B: series,precision,monthly,2020:1,2021:12

```
