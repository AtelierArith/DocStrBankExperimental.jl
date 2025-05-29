```
code_inferred(@nospecialize(f), t::Type...; 
        world = Base.get_world_counter(),
        interp = Core.Compiler.NativeInterpreter(world))
```

Derives a `Core.MethodInstance` specialization for signature `Tuple{typeof(f), t::Type...}` and infers it with `interp`. Can be used to derive inferred lowered code with custom interpreters, either as parts of custom compilation pipelines or for debugging purposes.

`code_inferred` includes explicit checks which prevent the user from inadvertedly running inference multiple times on the same cached `Core.CodeInfo` associated with the specialization.

!!! warning
    Inference and optimization are stateful – if you try to do "dumb" things like grab the inferred `Core.CodeInfo`, wipe it, and shove it through [`lambda`](@ref) ... it is highly unlikely to work and very likely to explode in your face.

    Inference also caches the inferred `Core.CodeInfo` associated with the `Core.MethodInstance` specialization *irrespective of the interpreter*. That means (at least as far as I know at this time) you can't quickly infer with multiple interpreters without forcing a cache invalidation in between inference runs.

