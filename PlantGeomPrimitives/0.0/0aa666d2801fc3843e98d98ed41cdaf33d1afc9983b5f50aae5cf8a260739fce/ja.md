```
scale!(m::Mesh, vec::Vec)
```

メッシュ `m` を `vec` で指定された3つの軸に沿ってスケーリングします。

# 引数

  * `m`: スケーリングされるメッシュ。
  * `vec`: x、y、および z 軸のスケーリング係数を含むベクトル。

# 例

```jldoctest
julia> m = Rectangle();

julia> scaling_vector = Vec(2.0, 1.5, 3.0);

julia> scale!(m, scaling_vector);
```
