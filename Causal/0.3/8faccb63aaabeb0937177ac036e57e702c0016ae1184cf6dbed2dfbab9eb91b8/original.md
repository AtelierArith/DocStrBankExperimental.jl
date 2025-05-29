```julia
launch(link)

```

Constructs a `taker` task and binds it to `link`. The `taker` task reads the data and prints an info message until `missing` is read from the `link`.
