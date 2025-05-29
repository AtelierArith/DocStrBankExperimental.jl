```
Point3D(x::Real,y::Real,z::Real; label="",pen=Pen())
Point3D(P; label="",pen=Pen())
```

三次元点を表すグラフィックスプリミティブです。

`P` は実数の3タプルまたは `Vec3` である可能性があります。

# 例

```julia-repl
julia> Point3D(0,4,5;pen="DarkGreen")
```
