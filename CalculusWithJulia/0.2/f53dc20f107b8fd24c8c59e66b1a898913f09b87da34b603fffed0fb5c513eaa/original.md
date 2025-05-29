```
D(f)
```

Function interface to `ForwardDiff.derivative`.

A method for `adjoint` for functions dispatches to `D`, so that the notation `f'` can be used to take the derivative of a function. (This is type piracy.)
