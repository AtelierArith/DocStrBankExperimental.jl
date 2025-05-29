```
apply(g::Graph, query::Query)
```

ユーザーが提供したクエリに一致するグラフ内のすべてのノードを含む配列を返します。

# 例

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> g = Graph(axiom = axiom);

julia> query = Query(A);

julia> apply(g, query);
```
