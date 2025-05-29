```julia
breakloop!(model, loop)
breakloop!(model, loop, breakpoint)

```

Breaks the algebraic `loop` of `model`. The `loop` of the `model` is broken by inserting a `Memory` at the `breakpoint` of loop.
