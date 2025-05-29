```
get_edgeval(e::AbstractValEdge, key)
```

エッジ `e` に対してキー `key` に付随する値を返します。

# 例

```jldoctest
julia> e = ValEdge(1, 2, (a=11.0, ));

julia> get_edgeval(e, 1) # 整数キーを使用
11.0

julia> get_edgeval(e, :a) # シンボリックキーを使用
11.0

```
