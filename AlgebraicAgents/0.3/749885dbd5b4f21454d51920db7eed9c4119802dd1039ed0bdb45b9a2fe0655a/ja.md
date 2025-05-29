```
delete_wires!(a; from, to, from_var_name, to_var_name)
```

2つのエージェントを接続するワイヤを削除します。オプションで、ソースおよびターゲット変数を指定できます。

# 例

```julia
delete_wires!(joint_system; from=alice, to=bob)
delete_wires!(joint_system; from=alice, to=bob, from_var_name="alice_x", to_var_name="bob_x")
```
