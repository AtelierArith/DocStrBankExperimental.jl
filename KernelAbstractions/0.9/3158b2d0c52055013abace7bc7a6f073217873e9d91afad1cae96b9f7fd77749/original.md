Get the typed IR for a kernel

# Examples

```
@ka_code_typed kernel(args. ndrange=...)
@ka_code_typed kernel(args. ndrange=... workgroupsize=...)
@ka_code_typed optimize=false kernel(args. ndrange=...)
```

To use interactive mode (with Cthulhu), call

```
@ka_code_typed interactive=true kernel(args. ndrange=...)
```

If ndrange is statically defined, then you could call

```
@ka_code_typed kernel(args.)
```

Works for CPU or CUDA kernels, with static or dynamic declarations
