```
meld(x)
```

Meldes a vector of edge/node. That means it tries to [`merge`](@ref) elements of the vector that relate to the same nodes.

# Example

```jldoctest
# `StenoGraphs` does not implement any `EdgeModifier`s
struct Weight{N <: Number} <: EdgeModifier w::N end;
e1 = Edge(Node(:a), Node(:b));
e2 = e1 * Weight(1.0);
e3 = UndirectedEdge(Node(:a), Node(:c));
e4 = UndirectedEdge(Node(:c), Node(:a));
es = [e1, e1, e2, e2, e3, e3, e4, e4]
meld(es) == [e2, e3]

# output

true
```
