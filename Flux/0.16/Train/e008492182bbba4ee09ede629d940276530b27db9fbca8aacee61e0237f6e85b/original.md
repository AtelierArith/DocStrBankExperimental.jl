```
train!(loss, model, data, opt_state)
```

Uses a `loss` function and training `data` to improve the `model`'s parameters according to a particular optimisation rule encoded in `opt_state`. Iterates through `data` once, evaluating for each `d in data` either `loss(model, d...)` if `d isa Tuple`, or else `loss(model, d)` for other `d`.

If `model` is an Enzyme.Duplicated and `Enzyme.jl` is loaded, gradients will be computed with Enzyme, otherwise they will be computed with Zygote.

For example, with these definitions...

```
data = [(x1, y1), (x2, y2), (x3, y3)]

loss3(m, x, y) = norm(m(x) .- y)        # the model is the first argument

opt_state = Flux.setup(Adam(), model)   # explicit setup of optimiser momenta
```

...calling `Flux.train!(loss3, model, data, opt_state)` runs a loop much like this:

```
for d in data
    ∂L∂m = gradient(loss3, model, d...)[1]
    update!(opt_state, model, ∂L∂m)
end
```

You can also write this loop yourself, if you need more flexibility. For this reason `train!` is not highly extensible. It adds only a few features to the loop above:

  * Stop with a `DomainError` if the loss is infinite or `NaN` at any point.
  * Show a progress bar using [`@withprogress`](https://github.com/JuliaLogging/ProgressLogging.jl).

!!! compat "New"
    This method was added in Flux 0.13.9. It has significant changes from the one used by Flux ≤ 0.13:

      * It now takes the `model` itself, not the result of `Flux.params`. (This is to move away from Zygote's "implicit" parameter handling, with `Grads`.)
      * Instead of `loss` being a function which accepts only the data, now it must also accept the `model` itself, as the first argument.
      * `opt_state` should be the result of [`Flux.setup`](@ref). Using an optimiser such as `Adam()` without this step should give you a warning.
      * Callback functions are not supported. (But any code can be included in the above `for` loop.)

