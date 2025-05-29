```
selective_eval_fromstart!([interp::Interpreter=RecursiveInterpreter()], frame, isrequired, istoplevel=false)
```

Like [`selective_eval!`](@ref), except it sets `frame.pc` to the first `true` statement in `isrequired`.
