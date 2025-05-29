```
intentplot(ibn::IBN, idx::Integer)
intentplot!(ax, ibn::IBN, idx::Integer)
```

Creates a tree plot of the intent Directed Acyclic Graph (DAG) `idx`.

## Attributes

  * `interdomain=false`: reach out to all domains (might malfunction)
  * `show_state=true`: shows the state of each intent DAG node
