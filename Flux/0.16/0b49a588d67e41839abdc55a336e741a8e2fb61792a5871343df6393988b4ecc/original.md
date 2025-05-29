```
PairwiseFusion(connection, layers...)
```

## Arguments

  * `connection`: A function taking 2 inputs and combining them into a single output
  * `layers`: The layers whose outputs are combined

## Inputs

This layer behaves differently based on input type:

1. If input `x` is a tuple of length N (or the input is `xs` with N `x`'s), matching the number of `layers`,

then each layer receives a new input `x[i]` combined with the previous output `y[i-1]` using `connection`.   Thus `(y1, y2, y3) = PairwiseFusion(connection, layer1, layer2, layer3)((x1, x2, x3))`   may be drawn as:

```
x1 → layer1 → y1 ↘
                  connection → layer2 → y2 ↘
              x2 ↗                          connection → layer3 → y3
                                        x3 ↗
```

... or written as:

```julia
y1 = layer1(x1)
y2 = layer2(connection(y1, x2))
y3 = layer3(connection(y2, x3))
```

2. With just one input, each layer receives the same `x` combined with the previous output. Thus `y = PairwiseFusion(connection, layers...)(x)` obeys:

```julia
y[1] == layers[1](x)
for i in 2:length(layers)
    y[i] == connection(layers[i](y[i-1]), x)
end
```

## Returns

A tuple of length N with the output of each fusion ((`y1`, `y2`, ..., `yN`) in the example above).
