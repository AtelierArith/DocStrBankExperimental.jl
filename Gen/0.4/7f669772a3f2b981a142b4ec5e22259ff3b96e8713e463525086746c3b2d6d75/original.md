```
grads::Tuple = logpdf_grad(dist::Distribution{T}, value::T, args...)
```

Compute the gradient of the logpdf with respect to the value, and each of the arguments.

If `has_output_grad` returns false, then the first element of the returned tuple is `nothing`. Otherwise, the first element of the tuple is the gradient with respect to the value. If the return value of `has_argument_grads` has a false value for at position `i`, then the `i+1`th element of the returned tuple has value `nothing`. Otherwise, this element contains the gradient with respect to the `i`th argument.
