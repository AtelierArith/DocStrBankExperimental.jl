```
@node(fformtype, sdtype, interfaces_list)
```

`@node` macro creates a node for a `fformtype` type object. To obtain a list of predefined nodes use `?is_predefined_node`.

# Arguments

  * `fformtype`: Either an existing type identifier, e.g. `Normal` or a function type identifier, e.g. `typeof(+)`
  * `sdtype`: Either `Stochastic` or `Deterministic`. Defines the type of the functional relationship
  * `interfaces_list`: Defines a fixed list of edges of a factor node, by convention the first element should be `out`. Example: `[ out, mean, variance ]`

Note: `interfaces_list` must not include names that contain `_` symbol in them, as it is reserved to identify joint posteriors around the node object.

# Examples

```julia

struct MyNormalDistribution
    mean :: Float64
    var  :: Float64
end

@node MyNormalDistribution Stochastic [ out, mean, var ]
```

```julia

@node typeof(+) Deterministic [ out, in1, in2 ]
```

# List of available nodes

See `?is_predefined_node`.
