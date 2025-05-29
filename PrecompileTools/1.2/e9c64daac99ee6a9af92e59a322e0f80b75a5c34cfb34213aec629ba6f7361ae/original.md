```
@setup_workload begin
    vars = ...
    ⋮
end
```

Run the code block only during package precompilation. `@setup_workload` is often used in combination with [`@compile_workload`](@ref), for example:

```
@setup_workload begin
    vars = ...
    @compile_workload begin
        y = f(vars...)
        g(y)
        ⋮
    end
end
```

`@setup_workload` does not force compilation (though it may happen anyway) nor intentionally capture runtime dispatches (though they will be precompiled anyway if the runtime-callee is for a method belonging to your package).
