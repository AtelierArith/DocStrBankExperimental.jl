```
keep(x)
```

Forces LLVM to keep a value alive, by pretending to clobber its memory. The memory is never actually accessed, which makes this a no-op in the final assembly.
