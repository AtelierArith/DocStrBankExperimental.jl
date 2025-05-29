```julia
struct DelayParentScope <: ModelingToolkit.SymScope
```

変数が、関与している方程式を持つシステムから少なくとも `N + 1` レベル上の階層に属していることを示します。これは最初の `N` 親によって名前空間が設定され、階層内の `N+1` 番目の親によって名前空間が設定されません。この時点以降の変数のスコープは `parent` によって与えられます。

言い換えれば、このスコープは `ParentScope` の適用を `N` レベル遅らせ、その間に `LocalScope` を適用します。

# フィールド

  * `parent::ModelingToolkit.SymScope`
  * `N::Int64`
