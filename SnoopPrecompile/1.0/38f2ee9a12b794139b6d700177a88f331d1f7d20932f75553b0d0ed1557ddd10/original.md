```
@precompile_setup begin
    vars = ...
    ⋮
end
```

Run the code block only during package precompilation. `@precompile_setup` is often used in combination with [`@precompile_all_calls`](@ref), for example:

```
@precompile_setup begin
    vars = ...
    @precompile_all_calls begin
        y = f(vars...)
        g(y)
        ⋮
    end
end
```

`@precompile_setup` does not force compilation (though it may happen anyway) nor intentionally capture runtime dispatches (though they will be precompiled anyway if the runtime-callee is for a method belonging to your package).
