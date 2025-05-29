```
rotatez!(m::Mesh, θ)
```

メッシュ `m` を z 軸周りに角度 `θ` だけ回転させます。

# 引数

  * `m`: スケーリングするメッシュ。
  * `θ`: ラジアン単位の回転角。

# 例

```jldoctest
julia> m = Rectangle();

julia> θ = pi/2;

julia> rotatez!(m, θ);
```
