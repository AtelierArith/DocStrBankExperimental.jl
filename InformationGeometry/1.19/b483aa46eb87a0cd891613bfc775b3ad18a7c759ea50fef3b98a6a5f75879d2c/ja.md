```
EmbeddedODESolution(sol::AbstractODESolution, Embedding::Function) -> AbstractODESolution
EmbeddedODESolution(sol::AbstractODESolution, PL::Plane) -> AbstractODESolution
```

解法 `sol(t)` を `Embedding∘sol` を介してより大きな空間にマッピングします。
