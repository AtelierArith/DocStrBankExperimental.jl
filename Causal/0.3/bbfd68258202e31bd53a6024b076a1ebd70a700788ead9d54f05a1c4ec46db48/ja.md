```julia
write!(writer, td, xd)

```

`xd`に対応する`xd`を`writer`のファイルに書き込みます。

# 例

```julia
julia> w = Writer(Inport(1))
Writer(path:/tmp/e907d6ad-8db2-4c4a-9959-5b8d33d32156.jld2, nin:1)

julia> open(w)
Writer(path:/tmp/e907d6ad-8db2-4c4a-9959-5b8d33d32156.jld2, nin:1)

julia> write!(w, 0., 10.)
10.0

julia> write!(w, 1., 20.)
20.0

julia> w.file
JLDFile /tmp/e907d6ad-8db2-4c4a-9959-5b8d33d32156.jld2 (read/write)
 ├─🔢 0.0
 └─🔢 1.0

julia> w.file[string(0.)]
10.0
```
