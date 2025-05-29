TriplewiseFusion(connection, layers...)

```
     u1                    u2
        ↘                     ↘
h1 → layer1 → connection → layer2 → connection
        ↗                     ↗
     v1                    v2
```

## Arguments

  * `connection`: A functio takes 3 inputs and combines them.
  * `layers`: `AbstractExplicitLayer`s or a `Chain`.

## Inputs

Layer behaves differently based on input type:

1. A tripe of `(h, u, v)`, where `u` and `v` itself are tuples of length `N`, the `layers` is also a tuple of length `N`. The computation is as follows

```julia
for i in 1:N
    h = connection(layers[i](h), u[i], v[i])
end
```

2. A triple of `(h, u, v)`, where `u` and `v` are `AbstractArray`s.

```julia
for i in 1:N
    h = connection(layers[i](h), u, v)
end
```

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N`

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N`
