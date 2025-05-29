```julia
struct GlobalScope <: ModelingToolkit.SymScope
```

階層内のどのサブシステムの方程式に関与していても、変数が階層のルートシステムに属することを示します。このスコープを持つ変数は名前空間に追加されることはなく、`complete`または`structural_simplify`を呼び出すときにのみシステムの未知数/パラメータに追加されます。
