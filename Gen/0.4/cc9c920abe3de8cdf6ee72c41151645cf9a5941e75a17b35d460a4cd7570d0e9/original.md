```
trace = simulate(gen_fn, args)
```

Execute the generative function and return the trace.

Given arguments (`args`), sample $(r, t) \sim p(\cdot; x)$ and return a trace with choice map $t$.

If `gen_fn` has optional trailing arguments (i.e., default values are provided), the optional arguments can be omitted from the `args` tuple. The generated trace  will have default values filled in.
