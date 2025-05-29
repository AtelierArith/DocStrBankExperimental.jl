```
(arg_grads, choice_values, choice_grads) = choice_gradients(
    trace, selection=EmptySelection(), retgrad=nothing)
```

Given a previous trace $(x, t)$ (`trace`) and a gradient with respect to the return value $∇_y J$ (`retgrad`), return the following gradient (`arg_grads`) with respect to the arguments $x$:

$$
∇_x \left( \log P(t; x) + J \right)
$$

The length of `arg_grads` will be equal to the number of arguments to the function that generated `trace` (including any optional trailing arguments). If an argument is not annotated with `(grad)`, the corresponding value in `arg_grads` will be `nothing`.

Also given a set of addresses $A$ (`selection`) that are continuous-valued random choices, return the folowing gradient (`choice_grads`) with respect to the values of these choices:

$$
∇_A \left( \log P(t; x) + J \right)
$$

The gradient is represented as a choicemap whose value at (hierarchical) address `addr` is $∂J/∂t[\texttt{addr}]$.

Also return the choicemap (`choice_values`) that is the restriction of $t$ to $A$.
