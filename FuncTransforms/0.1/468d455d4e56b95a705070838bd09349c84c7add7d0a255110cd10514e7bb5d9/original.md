```
VA(name::Symbol, drop::Int; gen = true)
```

A "VarArg". With `VA`, we can assign the values in this argument to the arguments of the transformed function.  `drop` would drop the given number of arguments of the transformed function (var"#self#" also counts).
