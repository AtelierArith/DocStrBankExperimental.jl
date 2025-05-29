```
translate!(m::Mesh, v::Vec)
```

メッシュ `m` をベクトル `v` によって移動します。

# 引数

  * `m`: 移動されるメッシュ。
  * `v`: メッシュを移動させるベクトル。

# 例

```jldoctest
julia> m = Rectangle();

julia> v = Vec(2.0, 1.5, 3.0);

julia> translate!(m, v);
```
