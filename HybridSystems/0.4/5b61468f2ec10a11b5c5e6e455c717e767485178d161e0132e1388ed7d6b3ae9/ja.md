```
has_transition(A::AbstractAutomaton, t::AbstractTransition)::Bool
```

オートマトン `A` が遷移 `t` を持っているかどうかを示す `Bool` を返します。

```
has_transition(A::AbstractAutomaton, q, r)::Bool
```

オートマトン `A` が状態 `q` から状態 `r` への遷移を持っているかどうかを示す `Bool` を返します。
