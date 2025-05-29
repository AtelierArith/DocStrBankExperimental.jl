```
terminate_child(sv, ls)
```

Tell a supervisor `sv` to remove a child `ls` from its  childs list and to terminate it with reason `:shutdown`.

# Arguments

  * `sv`: link or registered name of a supervisor,
  * `ls`: link or registered name of a child.
