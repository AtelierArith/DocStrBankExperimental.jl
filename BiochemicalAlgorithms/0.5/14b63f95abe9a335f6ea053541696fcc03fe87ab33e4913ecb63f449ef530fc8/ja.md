```
struct SystemComponentTable{T, C <: AbstractSystemComponent{T}} <: AbstractSystemComponentTable{T}
```

Tables.jl互換のシステムコンポーネントテーブルで、特定の`System{T}`およびシステムコンポーネント`C`（例：`Atom{T}`、`Bond{T}`など）用です。
