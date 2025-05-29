```
gen_fn = Map(kernel::GenerativeFunction)
```

Return a new generative function that applies the kernel independently for a vector of inputs.

The returned generative function has one argument with type `Vector{X}` for each argument of the input generative function with type `X`. The length of each argument, which must be the same for each argument, determines the number of times the input generative function is called (N). Each call to the input function is made under address namespace i for i=1..N. The return value of the returned function has type `FunctionalCollections.PersistentVector{Y}` where `Y` is the type of the return value of the input function. The map combinator is similar to the 'map' higher order function in functional programming, except that the map combinator returns a new generative function that must then be separately applied.

If `kernel` has optional trailing arguments, the corresponding `Vector` arguments can be omitted from calls to `Map(kernel)`.
