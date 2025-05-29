data(g::Graph)

グラフレベルの変数を返します。

## 例

```jldoctest
julia> struct A <: Node end;

julia> axiom = A();

julia> g = Graph(axiom = axiom, data = 2);

julia> data(g);
```
