```
tinf = @snoop_inference commands;
```

Produce a profile of julia's type inference, recording the amount of time spent inferring every `MethodInstance` processed while executing `commands`. Each fresh entrance to type inference (whether executed directly in `commands` or because a call was made by runtime-dispatch) also collects a backtrace so the caller can be identified.

`tinf` is a tree, each node containing data on a particular inference "frame" (the method, argument-type specializations, parameters, and even any constant-propagated values). Each reports the [`exclusive`](@ref)/[`inclusive`](@ref) times, where the exclusive time corresponds to the time spent inferring this frame in and of itself, whereas the inclusive time includes the time needed to infer all the callees of this frame.

The top-level node in this profile tree is `ROOT`. Uniquely, its exclusive time corresponds to the time spent *not* in julia's type inference (codegen, llvm_opt, runtime, etc).

Working with `tinf` effectively requires loading `SnoopCompile`.

!!! warning
    Note the semicolon `;` at the end of the `@snoop_inference` macro call. Because `SnoopCompileCore` is not permitted to invalidate any code, it cannot define the `Base.show` methods that pretty-print `tinf`. Defer inspection of `tinf` until `SnoopCompile` has been loaded.


# Example

```jldoctest; setup=:(using SnoopCompileCore), filter=r"([0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?/[0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?|\d direct)"
julia> tinf = @snoop_inference begin
           sort(rand(100))  # Evaluate some code and profile julia's type inference
       end;
```
