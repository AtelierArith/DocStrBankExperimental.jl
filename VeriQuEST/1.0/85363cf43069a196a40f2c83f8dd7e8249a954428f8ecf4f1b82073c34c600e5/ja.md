```
init_qubit(::TrapQubit)::Float64
```

この関数はメタグラフ内のキュービットを初期化するために使用されます。状態は指定されていませんが、トラップキュービットのプラス位相状態の角度が返されます。

# 引数

  * `trap::TrapQubit`: TrapQubitオブジェクト。

# 戻り値

  * トラップキュービットのプラス位相状態の角度を表すFloat64。

# 例

```julia
trap = TrapQubit()
angle = init_qubit(trap)
```
