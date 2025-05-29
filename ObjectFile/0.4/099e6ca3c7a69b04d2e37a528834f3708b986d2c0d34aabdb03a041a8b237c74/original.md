```
@mustimplement
```

Macro to create fallthrough implementations of basic functions such as `readheader(oh::ObjectHandle)`; these fallthrough implementations are meant to be overridden by methods in packages such as `ELF.jl` or `MachO.jl`.
