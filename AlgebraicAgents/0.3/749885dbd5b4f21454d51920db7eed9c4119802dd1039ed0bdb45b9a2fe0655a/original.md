```
delete_wires!(a; from, to, from_var_name, to_var_name)
```

Delete wires connecting two agents. Optionally, specify source and target variables.

# Examples

```julia
delete_wires!(joint_system; from=alice, to=bob)
delete_wires!(joint_system; from=alice, to=bob, from_var_name="alice_x", to_var_name="bob_x")
```
