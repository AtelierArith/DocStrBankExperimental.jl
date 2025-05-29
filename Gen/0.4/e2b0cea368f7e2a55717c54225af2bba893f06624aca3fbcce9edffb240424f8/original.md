```
(trace::U, weight) = generate(gen_fn::GenerativeFunction{T,U}, args::Tuple)
```

Return a trace of a generative function.

```
(trace::U, weight) = generate(gen_fn::GenerativeFunction{T,U}, args::Tuple,
                                constraints::ChoiceMap)
```

Return a trace of a generative function that is consistent with the given constraints on the random choices.

Given arguments $x$ (`args`) and assignment $u$ (`constraints`) (which is empty for the first form), sample $t \sim q(\cdot; u, x)$ and $r \sim q(\cdot; x, t)$, and return the trace $(x, r, t)$ (`trace`). Also return the weight (`weight`):

$$
\log \frac{p(r, t; x)}{q(t; u, x) q(r; x, t)}
$$

If `gen_fn` has optional trailing arguments (i.e., default values are provided), the optional arguments can be omitted from the `args` tuple. The generated trace  will have default values filled in.

Example without constraints:

```julia
(trace, weight) = generate(foo, (2, 4))
```

Example with constraint that address `:z` takes value `true`.

```julia
(trace, weight) = generate(foo, (2, 4), choicemap((:z, true))
```
