```
randflip!(config) -> (proposed_index, config)
randflip!(::FlipStyle, config) -> (proposed_index, config)
```

Flip the lattice configuration randomly using given flip style, default flip style is [`UniformFlip`](@ref){1}, which choose **one** site in the configuration uniformly and flip it.

One should always be able to use `config[proposed_index]` to get the current value of this lattice configuration. Whether one can change the site, depends on whether the configuration is stored in a mutable type.
