```
rotatey!(m::Mesh, θ)
```

メッシュ `m` を y 軸周りに角度 `θ` だけ回転させます。

# 引数

  * `m`: スケーリングするメッシュ。
  * `θ`: ラジアン単位の回転角。

# 例

```jldoctest
julia> m = Rectangle();

julia> θ = pi/2;

julia> rotatey!(m, θ);
```
