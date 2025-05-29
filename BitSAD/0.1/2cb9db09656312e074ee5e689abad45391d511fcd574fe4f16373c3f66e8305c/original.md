```
generatehw([io::IO = IOBuffer()], f, args...;
           top = nameof(f), submodules = [],
           transforms = [insertrng!, constantreduction!])
```

Generate a SystemVerilog module named `top` for `f(args...)` as a circuit. Apply `transforms` to the circuit before generating the SystemVerilog.
