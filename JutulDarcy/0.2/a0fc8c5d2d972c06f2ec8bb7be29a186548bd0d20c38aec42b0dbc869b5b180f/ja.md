```
flow_boundary_condition(cells, domain, pressures, temperatures = 298.15; kwarg...)
```

与えられた `domain` から `reservoir_domain` に来る `cells` のベクトルに流れ境界条件を追加します。入力引数 `pressures` と `temperatures` はスカラーまたはセルごとの値であることができます。他のキーワード引数は `FlowBoundaryCondition` コンストラクタに渡されます。

この関数の出力は、`forces = setup_reservoir_forces(model, bc = bc)` の形式で渡すことができる境界条件の `Vector` です。
