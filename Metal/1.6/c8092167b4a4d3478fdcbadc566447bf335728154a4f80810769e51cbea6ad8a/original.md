```
@metal threads=... groups=... [kwargs...] func(args...)
```

High-level interface for executing code on a GPU.

The `@metal` macro should prefix a call, with `func` a callable function or object that should return nothing. It will be compiled to a Metal function upon first use, and to a certain extent arguments will be converted and managed automatically using `mtlconvert`. Finally, a call to `mtlcall` is performed, creating a command buffer in the current global command queue then committing it.

There are a few keyword arguments that influence the behavior of `@metal`:

  * `launch`: whether to launch this kernel, defaults to `true`. If `false`, the returned kernel object should be launched by calling it and passing arguments again.
  * `name`: the name of the kernel in the generated code. Defaults to an automatically- generated name.
  * `queue`: the command queue to use for this kernel. Defaults to the global command queue.
