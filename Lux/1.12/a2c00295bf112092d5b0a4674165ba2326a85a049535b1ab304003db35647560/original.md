```
@compact(kw...) do x
    ...
    @return y # optional (but recommended for best performance)
end
@compact(kw...) do x, p
    ...
    @return y # optional (but recommended for best performance)
end
@compact(forward::Function; name=nothing, dispatch=nothing, parameters...)
```

Creates a layer by specifying some `parameters`, in the form of keywords, and (usually as a `do` block) a function for the forward pass. You may think of `@compact` as a specialized `let` block creating local variables that are trainable in Lux. Declared variable names may be used within the body of the `forward` function. Note that unlike typical Lux models, the forward function doesn't need to explicitly manage states.

Defining the version with `p` allows you to access the parameters in the forward pass. This is useful when using it with SciML tools which require passing in the parameters explicitly.

## Reserved Kwargs:

1. `name`: The name of the layer.
2. `dispatch`: The constructed layer has the type `Lux.CompactLuxLayer{dispatch}` which can be used for custom dispatches.

!!! tip
    Check the Lux tutorials for more examples of using `@compact`.


If you are passing in kwargs by splatting them, they will be passed as is to the function body. This means if your splatted kwargs contain a lux layer that won't be registered in the CompactLuxLayer. Additionally all of the device functions treat these kwargs as leaves.

## Special Syntax

  * `@return`: This macro doesn't really exist, but is used to return a value from the `@compact` block. Without the presence of this macro, we need to rely on closures which can lead to performance penalties in the reverse pass.

      * Having statements after the last `@return` macro might lead to incorrect code.
      * Don't do things like `@return return x`. This will generate non-sensical code like `<new var> = return x`. Essentially, `@return <expr>` supports any expression, that can be assigned to a variable.
      * Since this macro doesn't "exist", it cannot be imported as `using Lux: @return`. Simply use it in code, and `@compact` will understand it.
  * `@init_fn`: Provide a function that will be used to initialize the layer's parameters or state. See the docs of [`@init_fn`](@ref) for more details.
  * `@non_trainable`: Mark a value as non-trainable. This bypasses the regular checks and places the value into the state of the layer. See the docs of [`@non_trainable`](@ref) for more details.

# Extended Help

## Examples

Here is a linear model:

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=ones(3)) do x
           @return w .* x
       end
@compact(
    w = 3-element Vector{Float64},
) do x
    return w .* x
end       # Total: 3 parameters,
          #        plus 0 states.

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> r([1, 2, 3], ps, st)  # x is set to [1, 1, 1].
([1.0, 2.0, 3.0], NamedTuple())
```

Here is a linear model with bias and activation:

```jldoctest
julia> d_in = 5
5

julia> d_out = 3
3

julia> d = @compact(W=ones(d_out, d_in), b=zeros(d_out), act=relu) do x
           y = W * x
           @return act.(y .+ b)
       end
@compact(
    W = 3×5 Matrix{Float64},
    b = 3-element Vector{Float64},
    act = relu,
) do x
    y = W * x
    return act.(y .+ b)
end       # Total: 18 parameters,
          #        plus 1 states.

julia> ps, st = Lux.setup(Xoshiro(0), d);

julia> d(ones(5, 2), ps, st)[1] # 3×2 Matrix as output.
3×2 Matrix{Float64}:
 5.0  5.0
 5.0  5.0
 5.0  5.0

julia> ps_dense = (; weight=ps.W, bias=ps.b);

julia> first(d([1, 2, 3, 4, 5], ps, st)) ≈
       first(Dense(d_in => d_out, relu)([1, 2, 3, 4, 5], ps_dense, NamedTuple())) # Equivalent to a dense layer
true
```

Finally, here is a simple MLP. We can train this model just like any Lux model:

```jldoctest
julia> n_in = 1;

julia> n_out = 1;

julia> nlayers = 3;

julia> model = @compact(w1=Dense(n_in, 128),
           w2=[Dense(128, 128) for i in 1:nlayers], w3=Dense(128, n_out), act=relu) do x
           embed = act.(w1(x))
           for w in w2
               embed = act.(w(embed))
           end
           out = w3(embed)
           @return out
       end
@compact(
    w1 = Dense(1 => 128),               # 256 parameters
    w2 = NamedTuple(
        1 = Dense(128 => 128),          # 16_512 parameters
        2 = Dense(128 => 128),          # 16_512 parameters
        3 = Dense(128 => 128),          # 16_512 parameters
    ),
    w3 = Dense(128 => 1),               # 129 parameters
    act = relu,
) do x
    embed = act.(w1(x))
    for w = w2
        embed = act.(w(embed))
    end
    out = w3(embed)
    return out
end       # Total: 49_921 parameters,
          #        plus 1 states.

julia> ps, st = Lux.setup(Xoshiro(0), model);

julia> size(first(model(randn(n_in, 32), ps, st)))  # 1×32 Matrix as output.
(1, 32)

julia> using Optimisers, Zygote

julia> x_data = collect(-2.0f0:0.1f0:2.0f0)';

julia> y_data = 2 .* x_data .- x_data .^ 3;

julia> optim = Optimisers.setup(Adam(), ps);

julia> loss_initial = sum(abs2, first(model(x_data, ps, st)) .- y_data);

julia> for epoch in 1:1000
           loss, gs = Zygote.withgradient(
               ps -> sum(abs2, first(model(x_data, ps, st)) .- y_data), ps)
           Optimisers.update!(optim, ps, gs[1])
       end;

julia> loss_final = sum(abs2, first(model(x_data, ps, st)) .- y_data);

julia> loss_initial > loss_final
true
```

You may also specify a `name` for the model, which will be used instead of the default printout, which gives a verbatim representation of the code used to construct the model:

```jldoctest
julia> model = @compact(w=rand(3), name="Linear(3 => 1)") do x
           @return sum(w .* x)
       end
Linear(3 => 1)      # 3 parameters
```

This can be useful when using `@compact` to hierarchically construct complex models to be used inside a `Chain`.

!!! tip "Type Stability"
    If your input function `f` is type-stable but the generated model is not type stable, it should be treated as a bug. We will appreciate issues if you find such cases.


!!! warning "Parameter Count"
    Array Parameter don't print the number of parameters on the side. However, they do account for the total number of parameters printed at the bottom.

