```
Wrapper(
   default_args = Dict(
      :name => "ohe-wrapper",
      # Transformer to call.
      :transformer => OneHotEncoder(),
      # Transformer args.
      :transformer_args => Dict()
   )
)
```

Wraps around a transformer.

Implements `fit!` and `transform`.
