```
arg_grads = accumulate_param_gradients_determ!(
    gen_fn::CustomDetermGF, state, args, retgrad, scale_factor)
```

Increment gradient accumulators for parameters the gradient with respect to the arguments, optionally scaled, and return the gradient with respect to the arguments (not scaled).

Given the previous state and a gradient with respect to the return value $∇_y J$ (`retgrad`), return the following gradient (`arg_grads`) with respect to the arguments $x$:

$$
∇_x J
$$

Also increment the gradient accumulators for the trainable parameters $Θ$ of the function by:

$$
s * ∇_Θ J
$$

where $s$ is `scale_factor`.
