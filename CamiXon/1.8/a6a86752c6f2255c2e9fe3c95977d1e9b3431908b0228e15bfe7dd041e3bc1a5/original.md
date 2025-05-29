```
Shell(name, spinorbitals)
```

Type for specification of *closed electron shells* with fields:

  * `.name`: shell configuration (`::String`)
  * `.spinorbit`: Array of spinorbitals (`::Vector{Spinorbit}`)

The type `Shell` is best created with the function `castShell`.
