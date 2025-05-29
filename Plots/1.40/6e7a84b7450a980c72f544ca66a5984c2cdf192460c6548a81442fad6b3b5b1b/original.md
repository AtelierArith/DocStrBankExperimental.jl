Collect one frame per for-block iteration and return an `Animation` object.

Example:

```
p = plot(1)
anim = @animate for x=0:0.1:5
    push!(p, 1, sin(x))
end
gif(anim)
```

This macro supports additional parameters, that may be added after the main loop body.

  * Add `every n` with positive Integer n, to take only one frame every nth iteration.
  * Add `when <cond>` where `<cond>` is an Expression resulting in a Boolean, to take a    frame only when `<cond>` returns `true`. Is incompatible with `every`.
