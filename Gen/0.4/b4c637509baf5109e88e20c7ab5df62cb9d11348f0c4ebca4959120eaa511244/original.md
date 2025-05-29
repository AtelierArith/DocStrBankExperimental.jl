```
gen_fn = Unfold(kernel::GenerativeFunction)
```

Return a new generative function that applies the kernel in sequence, passing the return value of one application as an input to the next.

The kernel accepts the following arguments:

  * The first argument is the `Int` index indicating the position in the sequence (starting from 1).
  * The second argument is the *state*.
  * The kernel may have additional arguments after the state.

The return type of the kernel must be the same type as the state.

The returned generative function accepts the following arguments:

  * The number of times (N) to apply the kernel.
  * The initial state.
  * The rest of the arguments (not including the state) that will be passed to each kernel application.

The return type of the returned generative function is `FunctionalCollections.PersistentVector{T}` where `T` is the return type of the kernel.

If `kernel` has optional trailing arguments, the corresponding arguments can be omitted from calls to `Unfold(kernel)`.
