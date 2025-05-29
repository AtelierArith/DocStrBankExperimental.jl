```
split(root::LogicCircuit, (or, and)::Tuple{LogicCircuit, LogicCircuit}, var::Var; depth=0, sanity_check=true)
```

Return the circuit after spliting on edge `edge` and variable `var`
