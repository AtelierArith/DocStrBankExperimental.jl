```
@cuprint(xs...)
@cuprintln(xs...)
```

Print a textual representation of values `xs` to standard output from the GPU. The functionality builds on `@cuprintf`, and is intended as a more use friendly alternative of that API. However, that also means there's only limited support for argument types, handling 16/32/64 signed and unsigned integers, 32 and 64-bit floating point numbers, `Cchar`s and pointers. For more complex output, use `@cuprintf` directly.

Limited string interpolation is also possible:

```julia
    @cuprint("Hello, World ", 42, "\n")
    @cuprint "Hello, World $(42)\n"
```
