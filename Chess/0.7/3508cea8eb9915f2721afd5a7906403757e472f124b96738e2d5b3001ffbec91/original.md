```
findnodematching(node::GameNode, pred)
findnodematching(g::Game, pred)
```

Finds a node in the game tree that satisfies the predicate `pred`.

Returns a `GameNode`, or `nothing` if no node in the tree satisfies `pred`.
