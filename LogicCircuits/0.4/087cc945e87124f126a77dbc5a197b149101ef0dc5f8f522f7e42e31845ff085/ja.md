```
split(root::LogicCircuit, (or, and)::Tuple{LogicCircuit, LogicCircuit}, var::Var; depth=0, sanity_check=true)
```

エッジ `edge` と変数 `var` で分割した後の回路を返します。
