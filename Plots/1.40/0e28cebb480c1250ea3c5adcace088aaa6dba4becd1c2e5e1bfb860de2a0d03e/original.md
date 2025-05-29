Builds an `Animation` using one frame per loop iteration, then create an animated GIF.

Example:

```
  p = plot(1)
  @gif for x=0:0.1:5
    push!(p, 1, sin(x))
  end
```

This macro supports additional parameters, that may be added after the main loop body.

  * Add `fps=n` with positive Integer n, to specify the desired frames per second.
  * Add `every n` with positive Integer n, to take only one frame every nth iteration.
  * Add `when <cond>` where `<cond>` is an Expression resulting in a Boolean, to take a    frame only when `<cond>` returns `true`. Is incompatible with `every`.
