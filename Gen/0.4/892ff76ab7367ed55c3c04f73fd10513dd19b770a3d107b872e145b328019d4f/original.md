```
arg_grads = accumulate_param_gradients!(trace, retgrad=nothing, scale_factor=1.)
```

Increment gradient accumulators for parameters by the gradient of the log-probability of the trace, optionally scaled, and return the gradient with respect to the arguments (not scaled).

Given a previous trace $(x, t)$ (`trace`) and a gradient with respect to the return value $∇_y J$ (`retgrad`), return the following gradient (`arg_grads`) with respect to the arguments $x$:

$$
∇_x \left( \log P(t; x) + J \right)
$$

The length of `arg_grads` will be equal to the number of arguments to the function that generated `trace` (including any optional trailing arguments). If an argument is not annotated with `(grad)`, the corresponding value in `arg_grads` will be `nothing`.

Also increment the gradient accumulators for the trainable parameters $Θ$ of the function by:

$$
∇_Θ \left( \log P(t; x) + J \right)
$$
