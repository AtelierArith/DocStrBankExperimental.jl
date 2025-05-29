```
LangJulia(overwrite_input=true,inline=true,alloc_function,only_overwrite=false)
```

Code generation in julia language, with optional overwriting of input. The parameter `alloc_function` is a function of three parameters `alloc_function(k)` where `k` is the memory slot (default is `alloc_function(k)=similar(A,T)`). The `only_overwrite` specifies if `f` should be created if the overwrite funtion     `f!` contains the actual code.
