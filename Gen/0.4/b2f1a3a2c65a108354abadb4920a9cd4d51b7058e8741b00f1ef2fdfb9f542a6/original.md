```
req::Bool = accepts_output_grad(gen_fn::GenerativeFunction)
```

Return a boolean indicating whether the return value is dependent on any of the *gradient source elements* for any trace.

The gradient source elements are:

  * Any argument whose position is true in `has_argument_grads`
  * Any trainable parameter
  * Random choices made at a set of addresses that are selectable by `choice_gradients`.
