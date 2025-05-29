```
CompilerConfig(target, params; kernel=true, entry_abi=:specfunc, name=nothing,
                               always_inline=false)
```

Construct a `CompilerConfig` that will be used to drive compilation for the given `target` and `params`.

Several keyword arguments can be used to customize the compilation process:

  * `kernel`: specifies if the function should be compiled as a kernel (the default) or as a  plain function. This toggles certain optimizations, rewrites and validations.
  * `name`: the name that will be used for the entrypoint function. If `nothing` (the  default), the name will be generated automatically.
  * `entry_abi`: can be either `:specfunc` (the default), or `:func`.

      * `:specfunc` expects the arguments to be passed in registers, simple return values are returned in registers as well, and complex return values are returned on the stack using `sret`, the calling convention is `fastcc`.
      * The `:func` abi is simpler with a calling convention of the first argument being the function itself (to support closures), the second argument being a pointer to a vector of boxed Julia values and the third argument being the number of values, the return value will also be boxed. The `:func` abi will internally call the `:specfunc` abi, but is generally easier to invoke directly.
  * `always_inline` specifies if the Julia front-end should inline all functions into one if  possible.
  * `opt_level`: the optimization level to use (default: 2)
  * `libraries`: link the GPU runtime and `libdevice` libraries (default: true)
  * `optimize`: optimize the code (default: true)
  * `cleanup`: run cleanup passes on the code (default: true)
  * `validate`: enable optional validation of input and outputs (default: true)
  * `strip`: strip non-functional metadata and debug information (default: false)
