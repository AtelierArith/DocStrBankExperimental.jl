```
DataTable(data::T, opts::DataTableOptions)
```

---

### 例

---

```julia-repl
julia> df = DataFrame(a = sin.(-π:π/10:π), b = cos.(-π:π/10:π), c = string.(rand(21)))
julia> dt = DataTable(df)

または

julia> using TypedTables
julia> t = Table(a = [1, 2, 3], b = [2.0, 4.0, 6.0])
julia> dt = DataTable(t)

または

julia> using Tables
julia> Tables.table([1 2 3; 3 4 5], header = ["a", "b", "c"])
julia> dt = DataTable(t1)
```
