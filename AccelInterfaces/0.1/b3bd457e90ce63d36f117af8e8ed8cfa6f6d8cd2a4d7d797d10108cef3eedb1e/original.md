```
@jdiff [name] A B [clauses...] begin ... end
```

Analize difference between A and B

If `name` is not specified, this context can be accessed only as the currently active context.

# Arguments

  * `name`::String: a unique name for this accelerator context
  * `A`, `B`::Test cases

# Examples

```julia-repl
julia> @jdiff myacc fort_impl(USE_HIP=false) hip_impl(USE_HIP=true) begin
...
end
```

# Implementation

T.B.D.
