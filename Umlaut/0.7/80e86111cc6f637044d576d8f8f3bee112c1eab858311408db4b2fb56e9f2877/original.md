```
trace(f, args...; ctx=BaseCtx())
```

Trace function call, return the result and the corresponding Tape. `trace` records to the tape primitive methods and recursively dives into non-primitives.

Tracing can be customized using a context and the following methods:

  * isprimitive(ctx, f, args...) - decides whethere `f(args...)` should be treated as a primitive.
  * record*primitive!(tape::Tape{C}, v*f, v*args...) - records the primitive call defined by variables `f*v(v_args...)` to the tape.

The default context is `BaseCtx()`, which treats all functions from standard Julia modules as primitives and simply pushes the call to the tape. See the docstrings of these functions for further examples of customization.

# Examples:

```
foo(x) = 2x
bar(x) = foo(x) + 1

val, tape = trace(bar, 2.0)
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = *(2, %2)::Float64
#   %4 = +(%3, 1)::Float64
# )

val, tape = trace(bar, 2.0; ctx=BaseCtx([*, +, foo]))
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = foo(%2)::Float64
#   %4 = +(%3, 1)::Float64
# )

struct MyCtx end

isprimitive(ctx::MyCtx, f, args...) = isprimitive(BaseCtx(), f, args...) || f in [foo]
val, tape = trace(bar, 2.0; ctx=MyCtx())
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = foo(%2)::Float64
#   %4 = +(%3, 1)::Float64
# )
```
