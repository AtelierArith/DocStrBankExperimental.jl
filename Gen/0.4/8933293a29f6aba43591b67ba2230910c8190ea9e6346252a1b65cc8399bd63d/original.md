```
gen_fn = Switch(gen_fns::GenerativeFunction...)
```

Returns a new generative function that accepts an argument tuple of type `Tuple{Int, ...}` where the first index indicates which branch to call.

```
gen_fn = Switch(d::Dict{T, Int}, gen_fns::GenerativeFunction...) where T
```

Returns a new generative function that accepts an argument tuple of type `Tuple{Int, ...}` or an argument tuple of type `Tuple{T, ...}` where the first index either indicates which branch to call, or indicates an index into `d` which maps to the selected branch. This form is meant for convenience - it allows the programmer to use `d` like if-else or case statements.

`Switch` is designed to allow for the expression of patterns of if-else control flow. `gen_fns` must satisfy a few requirements:

1. Each `gen_fn` in `gen_fns` must accept the same argument types.
2. Each `gen_fn` in `gen_fns` must return the same return type.

Otherwise, each `gen_fn` can come from different modeling languages, possess different traces, etc.
