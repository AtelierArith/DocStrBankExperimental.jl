```
Parallel(connection, layers...)
Parallel(connection; name = layer, ...)
```

Create a layer which passes an input array to each path in `layers`, before reducing the output with `connection`.

Obeys the similar rules to broadcasting:

  * Called with one input `x`, this is equivalent to `connection([l(x) for l in layers]...)`.
  * With multiple `inputs` and just one layer, it is instead `connection([layer(x) for x in inputs]...)`.
  * With multiple inputs and multiple layers, one input is passed to each layer, thus `Parallel(+, f, g)(x, y) = f(x) + g(y)`.

Like [`Chain`](@ref), its sub-layers may be given names using the keyword constructor. These can be accessed by indexing: `m[1] == m[:name]` is the first layer.

See also [`SkipConnection`](@ref) which is `Parallel` with one `identity`, and [`Maxout`](@ref) which reduces by broadcasting `max`.

# Examples

```jldoctest
julia> p = Parallel(+, abs2, sqrt);

julia> p(3, 4)  # == 3^2 + √4, two functions two inputs
11.0

julia> p((3, 4))  # tuple is always splatted
11.0

julia> p(4)  # == 4^2 + √4, one input used twice
18.0

julia> Parallel(hcat, inv)(1, 2, 4)  # one function three inputs
1×3 Matrix{Float64}:
 1.0  0.5  0.25
```

With Flux layers:

```jldoctest
julia> model = Chain(Dense(3 => 5),
                     Parallel(vcat, Dense(5 => 4), Chain(Dense(5 => 7), Dense(7 => 4))),
                     Dense(8 => 17));

julia> model(rand32(3)) |> size
(17,)

julia> model2 = Parallel(+; α = Dense(10 => 2, tanh), β = Dense(5 => 2))
Parallel(
  +,
  α = Dense(10 => 2, tanh),             # 22 parameters
  β = Dense(5 => 2),                    # 12 parameters
)                   # Total: 4 arrays, 34 parameters, 344 bytes.

julia> model2(rand32(10), rand32(5)) |> size
(2,)

julia> model2[:α](rand32(10)) |> size
(2,)

julia> model2[:β] == model2[2]
true
```
