```
code_ircode_by_mi(f, mi::MethodInstance; world=get_world_counter(), interp=NativeInterpreter(world))
```

Return the `IRCode` object along with inferred return type.

# Arguments

  * `f(ir::IRCode, sv::OptimizationState) -> IRCode`: optimization passes to run.
  * `mi::MethodInstance`: method instance.

# Kwargs

  * `world::Int`: world number, default is calling `Core.Compiler.get_world_counter`.
  * `interp::AbstractInterpreter`: the interpreter to use for inference.
