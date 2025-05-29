```
AssignExpr(f::AssignExpr{L,R}; [lhs::L], [rhs::R], [allow_kw::Bool])
```

Returns a new copy of `f`, with optional `lhs`, `rhs`, and `allow_kw` overriden by the keyword arguments.
