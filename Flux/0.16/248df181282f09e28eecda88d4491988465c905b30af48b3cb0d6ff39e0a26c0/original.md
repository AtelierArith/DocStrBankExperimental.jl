```
Dropout(p; [dims, rng, active])
```

Layer implementing [dropout](https://arxiv.org/abs/1207.0580) with the given probability. This is used as a regularisation, i.e. to reduce overfitting.

While training, it sets each input to `0` (with probability `p`) or else scales it by `1 / (1 - p)`, using the [`NNlib.dropout`](@ref) function. While testing, it has no effect.

By default the mode will switch automatically, but it can also be controlled manually via [`Flux.testmode!`](@ref), or by passing keyword `active=true` for training mode.

By default every input is treated independently. With the `dims` keyword, instead it takes a random choice only along that dimension. For example `Dropout(p; dims = 3)` will randomly zero out entire channels on WHCN input (also called 2D dropout).

Keyword `rng` lets you specify a custom random number generator. (Only supported on the CPU.)

# Examples

```julia-repl
julia> m = Chain(Dense(ones(3,2)), Dropout(0.4))
Chain(
  Dense(2 => 3),                        # 9 parameters
  Dropout(0.4),
)

julia> m(ones(2, 7))  # test mode, no effect
3×7 Matrix{Float64}:
 2.0  2.0  2.0  2.0  2.0  2.0  2.0
 2.0  2.0  2.0  2.0  2.0  2.0  2.0
 2.0  2.0  2.0  2.0  2.0  2.0  2.0

julia> Flux.trainmode!(m)  # equivalent to use within gradient
Chain(
  Dense(2 => 3),                        # 9 parameters
  Dropout(0.4, active=true),
)

julia> m(ones(2, 7))
3×7 Matrix{Float64}:
 0.0      0.0      3.33333  0.0      0.0      0.0  0.0
 3.33333  0.0      3.33333  0.0      3.33333  0.0  3.33333
 3.33333  3.33333  0.0      3.33333  0.0      0.0  3.33333

julia> y = m(ones(2, 10_000));

julia> using Statistics

julia> mean(y)  # is about 2.0, same as in test mode
1.9989999999999961

julia> mean(iszero, y)  # is about 0.4
0.4003
```
