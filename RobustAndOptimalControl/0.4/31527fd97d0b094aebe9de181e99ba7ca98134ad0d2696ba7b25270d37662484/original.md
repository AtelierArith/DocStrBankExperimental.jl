```
add_input_differentiator(sys::StateSpace, ui = 1:sys.nu; goodwin=false)
```

Augment the output of `sys` with the difference `u(k+1)-u(k)`

# Arguments:

  * `ui`: An index or vector of indices indicating which inputs to differentiate.
  * `goodwin`: If true, the difference operator will use the Goodwin δ operator, i.e., `(u(k+1)-u(k)) / sys.Ts`.

The augmented system will have the matrices

```
[A 0; 0 0]  [B; I]  [C 0; 0 -I]  [D; I]
```

with `length(ui)` added states and outputs.
