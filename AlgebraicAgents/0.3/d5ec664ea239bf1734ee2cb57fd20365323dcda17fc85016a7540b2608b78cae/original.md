```
add_wire!(a; from, to, from_var_name, to_var_name)
```

Add a wire connecting two agents.

# Examples

```julia
add_wire!(joint_system; from=alice, to=bob, from_var_name="alice_x", to_var_name="bob_x")
```
