```
compile(target::Symbol, job::CompilerJob)
```

Compile a `job` to one of the following formats as specified by the `target` argument: `:julia` for Julia IR, `:llvm` for LLVM IR and `:asm` for machine code.
