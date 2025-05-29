```
@head_default f([io::IO=stdout], a::Int, b=0)
```

Generate a function `f` that has default values for the arguments at the beginning of the argument list. Note that you need to specify the types of some arguments to prevent ambiguity.

It is usually recommended to only default at most one argument that has a unique type.

The above is equivalent to

```julia
f(io::IO, a::Int) = f(io, a, 0)
f(a::Int, b) = f(stdout, a, b)
f(a::Int) = f(stdout, a, 0)
```

You can also use `@head_default` before a function definition.
