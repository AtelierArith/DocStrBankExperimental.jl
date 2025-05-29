```
convert(LLVMType, typ::Type; allow_boxed=true)
```

Convert a Julia type `typ` to its LLVM representation in the current context. The `allow_boxed` argument determines whether boxed types are allowed.
