```
add_wire!(a; from, to, from_var_name, to_var_name)
```

2つのエージェントを接続するワイヤを追加します。

# 例

```julia
add_wire!(joint_system; from=alice, to=bob, from_var_name="alice_x", to_var_name="bob_x")
```
