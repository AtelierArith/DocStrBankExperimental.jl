```
assert_flow(::BackwardFlow, resource::MBQCResourceState, vertex::Int64)
```

MBQCリソース状態における逆流の特性を確認します。

引数:

  * `::BackwardFlow`: 逆流のタイプ。
  * `resource::MBQCResourceState`: MBQCリソース状態。
  * `vertex::Int64`: チェックされる頂点。

この関数は、逆流の以下の特性を確認します：

1. 指定された頂点の流れがリソース状態の頂点集合に含まれている。
2. 指定された頂点が指定された頂点の流れの近傍に含まれている。
3. 指定された頂点が指定された頂点の流れの近傍にあるすべての頂点以下である。

特性が違反されると、適切なメッセージでエラーをスローします。

# 例

```julia
assert_flow(BackwardFlow(), resource, vertex) # 逆流の特性を確認します
```
