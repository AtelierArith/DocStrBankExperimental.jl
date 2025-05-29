```
shell(tr::Transition)
```

Return the shell (Shell(1), Shell(2),...) associated with the transition's inner shell.

Example:

```
@assert shell(n"K-L3")==Shell(1)
@assert shell(n"M5-N7")==Shell(3)
```
