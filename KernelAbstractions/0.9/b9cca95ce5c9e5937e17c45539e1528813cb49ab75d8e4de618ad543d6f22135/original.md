Get the llvm code for a kernel

# Examples

```
@ka_code_llvm kernel(args. ndrange=...)
@ka_code_llvm kernel(args. ndrange=... workgroupsize=...)
@ka_code_llvm optimize=false kernel(args. ndrange=...)
```

If ndrange is statically defined, then you could call

```
@ka_code_llvm kernel(args.)
```

Works for CPU kernels ONLY, with static or dynamic declarations
