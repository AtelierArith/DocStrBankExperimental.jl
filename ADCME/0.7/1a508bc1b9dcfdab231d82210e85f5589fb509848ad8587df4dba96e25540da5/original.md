```
AdamOptimizer(learning_rate=1e-3;kwargs...)
```

Constructs an ADAM optimizer. 

# Example

```julia
learning_rate = 1e-3
opt = AdamOptimizer(learning_rate).minimize(loss)
sess = Session(); init(sess)
for i = 1:1000
    _, l = run(sess, [opt, loss])
    @info "Iteration $i, loss = $l")
end
```

# Dynamical Learning Rate

We can also use dynamical learning rate. For example, if we want to use a learning rate $l_t = \frac{1}{1+t}$, we have 

```julia
learning_rate = placeholder(1.0)
opt = AdamOptimizer(learning_rate).minimize(loss)
sess = Session(); init(sess)
for i = 1:1000
    _, l = run(sess, [opt, loss], lr = 1/(1+i))
    @info "Iteration $i, loss = $l")
end
```

The usage of other optimizers such as [`GradientDescentOptimizer`](@ref), [`AdadeltaOptimizer`](@ref), and so on  is similar: we can just replace `AdamOptimizer` with the corresponding ones. 
