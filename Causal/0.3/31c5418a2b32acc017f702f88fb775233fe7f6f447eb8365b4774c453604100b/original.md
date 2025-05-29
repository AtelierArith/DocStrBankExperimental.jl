```julia
approve!(comp)

```

Read `handshake` link of `comp`. When not approved or `false` is read from the `handshake` link, the task launched for the `trigger` link of `comp` gets stuck during `comp` is taking step.
