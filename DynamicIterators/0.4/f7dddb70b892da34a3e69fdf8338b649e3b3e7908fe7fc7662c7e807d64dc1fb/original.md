```
Evolution
```

Evolutions define

```
    evolve(iter, value::T)::T
```

and possibly

```
    evolve(iter, key=>value)
```

They guarantee `HasEltype()` and `eltype(iter) == T`.
