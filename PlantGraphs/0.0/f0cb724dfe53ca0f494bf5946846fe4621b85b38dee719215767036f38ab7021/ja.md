```
rules(g::Graph)
```

動的グラフに格納されたすべてのグラフ書き換えルールを含むタプルを返します

## 例

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> rule = Rule(A, rhs = x -> A() + B());

julia> rules_graph = Graph(axiom = axiom, rules = rule);

julia> rules(rules_graph);
```
