```
@precompile_all_calls f(args...)
```

`precompile` any method-calls that occur inside the expression. All calls (direct or indirect) inside a `@precompile_all_calls` block will be precompiled.

`@precompile_all_calls` has three key features:

1. code inside runs only when the package is being precompiled (i.e., a `*.ji` precompile cache file is being written)
2. the interpreter is disabled, ensuring your calls will be compiled
3. both direct and indirect callees will be precompiled, even for methods defined in other packages and even for runtime-dispatched callees (requires Julia 1.8 and above).

!!! note
    For comprehensive precompilation, ensure the first usage of a given method/argument-type combination occurs inside `@precompile_all_calls`.

    In detail: runtime-dispatched callees are captured only when type-inference is executed, and they are inferred only on first usage. Inferrable calls that trace back to a method defined in your package, and their *inferrable* callees, will be precompiled regardless of "ownership" of the callees (Julia 1.8 and higher).

    Consequently, this recommendation matters only for:

    ```
    - direct calls to methods defined in Base or other packages OR
    - indirect runtime-dispatched calls to such methods.
    ```

