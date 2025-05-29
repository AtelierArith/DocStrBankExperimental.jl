```
sconnect(input::Function, sys::T; name)
sconnect(input::Num,      sys::T; name)
```

Connect a function `input(t)` to `sys.input`

# Examples:

```julia
sconnect(sin, sys)   # Connect a funciton, assumed to be a function of time
sconnect(sin(t), sys) # Connect a Num
```
