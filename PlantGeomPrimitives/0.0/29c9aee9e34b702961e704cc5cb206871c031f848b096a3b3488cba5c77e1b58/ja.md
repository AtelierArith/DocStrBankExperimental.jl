```
Mesh(meshes)
```

複数のメッシュを1つにマージします

# 引数

  * `meshes`: マージするメッシュのベクター。

# 戻り値

すべての入力メッシュをマージした結果の新しい `Mesh` オブジェクト。

# 例

```jldoctest
julia> e = Ellipse(length = 2.0, width = 2.0, n = 10);

julia> r = Rectangle(length = 10.0, width = 0.2);

julia> m = Mesh([e,r]);
```
