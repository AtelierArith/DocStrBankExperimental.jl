```
BBox(m::Mesh)
```

メッシュオブジェクトの周りにタイトな軸整列バウンディングボックスを構築します。

# 引数

  * `m`: バウンディングボックスを構築するメッシュ。

# 例

```jldoctest
julia> m = Rectangle();

julia> box = BBox(m);
```
