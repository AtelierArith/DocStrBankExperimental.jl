```
ノード
```

グラフ内のすべてのノードが継承すべき抽象型です。これにより、グラフ構築DSLを使用できます。

# 例

```jldoctest
julia> struct bar <: Node
           x::Int
       end;

julia> b1 = bar(1);

julia> b2 = bar(2);

julia> b1 + b2;
```
