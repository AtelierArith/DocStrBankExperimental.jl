```
transport(plan::Coupling, i, j; conditional = false)
transport(plan::Coupling, (i, j); conditional = false)

transport(plan::Coupling, is, js; conditional = false)
transport(plan::Coupling, (is, js); conditional = false)

transport(ws::Workspace, a, b, i, j; conditional = false)
transport(ws::Workspace, a, b, (i, j); conditional = false)

transport(ws::Workspace, a, b, is, js; conditional = false)
transport(ws::Workspace, a, b, (is, js); conditional = false)
```

Returns the evaluation of the coupling `plan` at pixel `(i,j)` of node `a`. If iterables `is` and `js` are provided, a vector of transport arrays is returned.

If `conditional = true`, the transport arrays sum to one.

If a workspace `ws` as well as two nodes `a` and `b` are provided, the corresponding coupling is calculated implicitly.
