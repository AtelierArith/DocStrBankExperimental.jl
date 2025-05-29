```julia
struct LocalScope <: ModelingToolkit.SymScope
```

変数のデフォルトスコープです。それは、関与する方程式を持つシステムに属し、階層の各レベルによって名前空間が分けられています。
