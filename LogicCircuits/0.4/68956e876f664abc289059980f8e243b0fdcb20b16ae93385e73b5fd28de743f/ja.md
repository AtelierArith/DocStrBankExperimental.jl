```
conjoin(root::LogicCircuit, lit::Lit; callback::Function)
```

与えられたリテラル制約と共に結合された回路を返します。`callback`は結合ノードを修正した後に呼び出されます。
