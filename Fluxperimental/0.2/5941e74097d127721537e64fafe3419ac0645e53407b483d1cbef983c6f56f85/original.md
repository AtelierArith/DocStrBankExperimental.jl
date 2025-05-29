```
@compact(forward::Function; name=nothing, parameters...)
```

Creates a layer by specifying some `parameters`, in the form of keywords, and (usually as a `do` block) a function for the forward pass. You may think of `@compact` as a specialized `let` block creating local variables  that are trainable in Flux. Declared variable names may be used within the body of the `forward` function.

Here is a linear model:

```
r = @compact(w = rand(3)) do x
  w .* x
end
r([1, 1, 1])  # x is set to [1, 1, 1].
```

Here is a linear model with bias and activation:

```
d_in = 5
d_out = 7
d = @compact(W = randn(d_out, d_in), b = zeros(d_out), act = relu) do x
  y = W * x
  act.(y .+ b)
end
d(ones(5, 10)) # 7×10 Matrix as output.
d([1,2,3,4,5]) ≈ Dense(d.variables.W, zeros(7), relu)([1,2,3,4,5]) # Equivalent to a dense layer
```

```

Finally, here is a simple MLP:

```

using Flux

n*in = 1 n*out = 1 nlayers = 3

model = @compact(   w1=Dense(n*in, 128),   w2=[Dense(128, 128) for i=1:nlayers],   w3=Dense(128, n*out),   act=relu ) do x   embed = act(w1(x))   for w in w2     embed = act(w(embed))   end   out = w3(embed)   return out end

model(randn(n_in, 32))  # 1×32 Matrix as output.

```

We can train this model just like any `Chain`:

```

data = [([x], 2x-x^3) for x in -2:0.1f0:2] optim = Flux.setup(Adam(), model)

for epoch in 1:1000   Flux.train!((m,x,y) -> (m(x) - y)^2, model, data, optim) end ```To specify a custom printout for the model, you may find [`NoShow`](@ref) useful.
