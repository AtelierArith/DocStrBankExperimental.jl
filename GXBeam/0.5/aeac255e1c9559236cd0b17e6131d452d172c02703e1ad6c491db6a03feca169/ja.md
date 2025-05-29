```
AssemblyState(system, assembly; prescribed_conditions = Dict())
AssemblyState(x, system, assembly; prescribed_conditions = Dict())
AssemblyState(dx, x, system, assembly; prescribed_conditions = Dict())
```

システム状態を、状態ベクトル `x` と速度ベクトル `dx` に基づいて後処理します。時間ステップのアセンブリの状態を定義する `AssemblyState` 型のオブジェクトを返します。

`prescribed_conditions` が提供されていない場合、すべての点状態変数は、分析で使用される実際のアイデンティティではなく、変位/回転であると見なされます。
