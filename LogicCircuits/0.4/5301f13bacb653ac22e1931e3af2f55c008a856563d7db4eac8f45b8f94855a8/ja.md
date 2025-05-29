```
model_count(root::LogicCircuit, num_vars_in_scope::Int = num_variables(root))::BigInt
```

回路のモデル数を取得します。`num_vars_in_scope`は回路内の変数の数に設定されていますが、回路内で全ての変数が言及されていない場合など、異なる値を設定する必要があることがあります。
