```julia
struct ParentScope <: ModelingToolkit.SymScope
```

この変数は、それが関与する方程式のシステムに属していないことを示します。このシステムによって名前空間が設定されていません。このシステムの直上の親において、この変数のスコープは `parent` によって与えられます。

# フィールド

  * `parent::ModelingToolkit.SymScope`
