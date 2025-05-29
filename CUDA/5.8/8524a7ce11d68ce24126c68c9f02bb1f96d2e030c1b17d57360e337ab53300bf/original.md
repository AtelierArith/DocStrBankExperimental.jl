```
CuModule(data, options::Dict{CUjit_option,Any})
CuModuleFile(path, options::Dict{CUjit_option,Any})
```

Create a CUDA module from a data, or a file containing data. The data may be PTX code, a CUBIN, or a FATBIN.

The `options` is an optional dictionary of JIT options and their respective value.
